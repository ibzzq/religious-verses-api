<p align="center">
  <img src="https://github.com/ibzzq/religious-verses-api/blob/main/religious-verses-logo.png?raw=true"
       alt="Religious Verses API Logo"
       width="75%"
       height="50%">
</p>

<h1 align="center">Religious Verses API</h1>


Religious Verses API is a lightweight and easy-to-use API that delivers a quick dose of spiritual inspiration that also allows you to get closer to your religion with just a quick 5 seconds read. Perfect for personal reflection, learning, or integrating into apps, websites, or bots. I currently do intend on adding more religious texts, please let me know!

---

## Features

- Get a **random verse** from the Qur'an, Bible, or Torah from the [designated verse list](https://github.com/ibzzq/religious-verses-api/tree/main/List%20of%20Verses)
- There are currently **365 verses** for each religious source of wisdom
- Glance YML Cache set to 1 Day *(modifiable)*
- **Fast and simple** API hosted on my domain with **Cloudflare**
- Easy to integrate into apps, websites, or home projects.

---
## The API itself
- The API themselves are currently hosted at: *quran.ibzz.uk - bible.ibzz.uk - torah.ibzz.uk*
- These URLs have a worker route within Cloudflare, but are *exposed perfectly*
- Hosted in Cloudflare with KV worker application databases

https://quran.ibzz.uk
https://bible.ibzz.uk
https://torah.ibzz.uk

## Example Usage
This API works tremendously well with many use cases. Personally, I use the API with the [Glance Dashboard](https://github.com/glanceapp/glance) through the [Custom Glance YML Provided](https://github.com/ibzzq/religious-verses-api/tree/main/Glance%20YMLs) where it can be aesthetically displayed on my [Glance Dashboard](https://github.com/glanceapp/glance). Here are some examples of what it may look like within the webpage dashboard as a custom widget. I mention Glance a lot throughout these docs, but please note that this API can also be used for:
- [Home Assistant](https://www.home-assistant.io/) dashboards (Markdown or custom cards pulling REST data)
- Kiosk displays (wall tablets, Pi screens, [Immich-Kiosk styled setups](https://github.com/damongolding/immich-kiosk))
- Lock-screen widgets or desktop widgets
- Terminal dashboards

![Screenshot of Glance Dashboard Widget](https://github.com/ibzzq/religious-verses-api/blob/main/Screenshots%20of%20Glance/smaller-vertical-stack.png?raw=true)

Here is the Qur'an YML example that is ready to be dropped into [Glance](https://github.com/glanceapp/glance). The **others** can be found [here](https://github.com/ibzzq/religious-verses-api/tree/main/Glance%20YMLs) at the Glance YML Folder
```
          - type: custom-api
            title: Qur'an Verse
            cache: 1d
            url: https://quran.ibzz.uk
            template: |
              <p class="size-h4 color-paragraph" style="font-weight:600; direction: rtl; text-align: right;">
                {{ .JSON.String "title" }}
              </p>
              <p class="size-h6 color-dimmed" style="direction: rtl; text-align: right;">
                {{ .JSON.String "description" }}
              </p>
```
## How it works
The API returns JSON text which looks like this.
```{
  "title": "The religious scripture here",
  "description": "May either return the translation OR the source. See note below.",
  "color": "white"
}
```
The 'colour' doesn't have an effect in [Glance](https://github.com/glanceapp/glance) as the colour scheme for the entire page is determined by the user upon Glance deployment and cannot be overriden by the API 'colour' settings.
### Note
The 'description' varies across the holy books. For the Qur'an and Torah, it serves as the translation into ENGLISH from the original scripture language **(as either Arabic or Hebrew)**. For the **Bible**, however, it returns the source of the quote from within the Bible, where it may be found. This is because the Qur'an and Torah are often read in its original language of origin. On the other hand, the Bible is often shared in English.

---
*This API provides religious verses for educational, personal, or research use. Please respect the integrity of the texts. Please note that some translations may not be 100% accurate. Some quotes from the API may also not be directly as stated in original texts due to translation misinterpretations. Commercial or altered distribution of the texts or quotes themselves is seriously discouraged.*
