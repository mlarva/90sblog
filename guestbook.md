---
layout: default
title: "Guestbook"
header_title: "Sign My Guestbook!"
header_subtitle: "Leave a message for all the world to see!"
---

## Previous Guestbook Entries

<div class="guestbook-entry">
    <div class="entry-header">From: CyberSurfer95 | Email: coolkid@aol.com | Date: Dec 4, 1995</div>
    <p>Awesome page dude! Your HTML skills are totally rad. Can't wait to see what you add next. Maybe some scrolling text? That would be so cool!</p>
    <p>BTW, check out my page at geocities.com/area51/vault/1234 - I just added a new animated under construction GIF!</p>
</div>

<div class="guestbook-entry">
    <div class="entry-header">From: NetNinja | Email: hacker@university.edu | Date: Dec 3, 1995</div>
    <p>Nice work on the page layout! I'm impressed with your use of tables for formatting. You should totally add a hit counter and maybe a MIDI background song.</p>
    <p>Keep up the great work exploring cyberspace! 🚀</p>
</div>

<div class="guestbook-entry">
    <div class="entry-header">From: DialUpDave | Email: dave.jones@bigcorp.com | Date: Dec 2, 1995</div>
    <p>Found your page through Yahoo! directory. Great stuff! Your blog posts about the future of the internet are fascinating. Who knows, maybe someday we'll even have portable computers that can access the web!</p>
    <p>Peace out!</p>
</div>

<div class="guestbook-entry">
    <div class="entry-header">From: WebWanderer | Email: wanderer@prodigy.net | Date: Dec 1, 1995</div>
    <p>Hello from the other side of the information superhighway! Your page loaded super fast on my 14.4k modem. Thanks for keeping the images small!</p>
    <p>Have you tried that new search engine called "AltaVista"? It's supposed to be even better than Yahoo!</p>
</div>

## Sign My Guestbook!

<form name="guestbook" method="POST" data-netlify="true" action="/thanks/">
    <table>
        <tr>
            <td><b>Your Name:</b></td>
            <td><input type="text" name="name" size="30" required></td>
        </tr>
        <tr>
            <td><b>Email Address:</b></td>
            <td><input type="email" name="email" size="30"></td>
        </tr>
        <tr>
            <td><b>Homepage URL:</b></td>
            <td><input type="url" name="homepage" size="30" value="http://"></td>
        </tr>
        <tr>
            <td><b>Your Message:</b></td>
            <td><textarea name="message" rows="5" cols="40" required></textarea></td>
        </tr>
        <tr>
            <td colspan="2" align="center">
                <input type="submit" value="Sign Guestbook!">
                <input type="reset" value="Clear Form">
            </td>
        </tr>
    </table>
</form>

<p><small><i>Note: If you deploy to Netlify, this form will actually work and send you emails! For GitHub Pages, it's just for show (like the original 90s experience).</i></small></p>