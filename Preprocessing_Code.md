# Preprocessing Node

## Purpose
Extracts and cleans email content from Gmail API responses, preparing it for spam detection APIs.

## Location
**Node Name:** Code (First preprocessing node after "Get a message")

```
return items.map(item => {
    const email = item.json;

    // Format "From"
    let from = "";
    if (email.from && email.from.value && email.from.value.length > 0) {
        const sender = email.from.value;
        from = sender.address;
    }

    // Subject
    const subject = email.subject || email.original_subject || "";

    // Body extraction
    let body = email.text || "";
    if (!body && email.html) {
        body = email.html.replace(/<style[^>]*>[\s\S]*?<\/style>/gi, " ");
        body = body.replace(/<[^>]+>/g, " ");
        body = body.replace(/&nbsp;/gi, " ");
        body = body.replace(/&amp;/gi, "&");
        body = body.replace(/&lt;/gi, "<");
        body = body.replace(/&gt;/gi, ">");
    }

    body = body.replace(/^\d+\s*/, "");
    body = body.replace(/\s+/g, " ").trim();
    body = body.replace(/unsubscribe.*$/i, "")
               .replace(/copyright.*$/i, "");

    const MAX_CHARS = 9000;
    if (body.length > MAX_CHARS) {
        body = body.slice(0, MAX_CHARS) + " …[truncated]";
    }

    const message = `Subject: ${subject}\n\n${body}`;

    return {
        json: {
            message,
            original_subject: subject,
            from
        }
    };
});
```
```
