---
title: Home
media_order: 'nhaTam.jpg,P1210039.jpg,P1210045.jpg,moving_1.jpg,thanghoa.jpg,CT.jpg,Easter2018.jpg,aovang.jpg,dangTG_MC.jpg,notes.png'
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
body_classes: landing-page
creator: hieuliem
api: AIzaSyBrRni2mwM41hhwOFSZfGtOQcLS-Ky8Jdg
icon: '<i class="material-icons">home</i>'
yt_channel: UCiySdBJvYT0DPgUe34Z-yzw
yt_video: 6U7h66ht5_U
future_countdown: 'December 2, 2018 03:24:00'
callout: ''
callout_bg: notes.png
showcase_title: Testing
showcase_subtitle: 'Kỷ niệm 30 năm Các Thánh Tử Đạo Việt Nam<br>Kỷ niệm 19 năm Cung Hiến Thánh Đường<br>Bổn Mạng Giáo Xứ - Mùa Hè Hồng Ân'
button_text: 'Live Stream'
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
