---
title: Home
media_order: 'P1210045.jpg,P1210039.jpg,moving_1.jpg,thanghoa.jpg,CT.jpg,Easter2018.jpg,aovang.jpg,dangTG_MC.jpg,notes.png'
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
body_classes: landing-page
creator: admin
icon: '<i class="material-icons">home</i>'
yt_channel_: zMdNqG3TV6c
callout: 'https://thanhca.chungnhan.org'
callout_bg: notes.png
showcase_title: 'Phụng Vụ Thánh Ca'
showcase_subtitle: 'Thánh Vinh Đáp Ca Trong Tuần'
button_text: thanhca.chungnhan.org
form:
    name: contact-form
    action: /home
    fields:
        -
            name: name
            id: name
            label: Name
            classes: 'form-control form-control-lg'
            placeholder: 'Your name'
            autocomplete: 'on'
            type: text
            validate:
                required: true
        -
            name: email
            id: email
            classes: 'form-control form-control-lg'
            label: Email
            placeholder: 'Enter your email address'
            type: email
            validate:
                rule: email
                required: true
        -
            name: message
            label: Message
            classes: 'form-control form-control-lg'
            size: long
            placeholder: 'Enter your message'
            type: textarea
            validate:
                required: true
        -
            name: g-recaptcha-response
            label: Captcha
            type: captcha
            recaptcha_site_key: 6LfFuUwUAAAAAFb7eHxFFdOhsJiQCcXTsVyDt6M6
            recaptcha_not_validated: 'Captcha not valid!'
            validate:
                required: true
    buttons:
        -
            type: submit
            value: Submit
            classes: 'btn btn-primary btn-block'
    process:
        -
            captcha:
                recatpcha_secret: 6LfFuUwUAAAAALR-On9g0q7PjnlY_47Q4_Mxwz4S
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to:
                    - '{{ config.plugins.email.from }}'
                    - '{{ form.value.email }}'
                subject: '[Feedback] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: feedback-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Thank you for your feedback!'
        -
            display: thankyou
---

# Contact form
