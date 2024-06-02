# hacked-jekyll

Hacked Jekyll is a responsive, minimalistic Jekyll theme for a tiny personal website. It consists of a homepage and a 404 page. The homepage lists information about the user in a format that resembles JSON, giving the website a "hacked" appearance. As in JSON, elements can be strings, arrays, or hashes. One of the string elements, typically the user's description, can use [typed.js](https://mattboldt.com/demos/typed-js/) to cycle through multiple lines of text.

The style is rebooted through [normalize.css](https://necolas.github.io/normalize.css/) and based on the [Open Color](https://yeun.github.io/open-color/) library. The monospaced typeface [Hack](https://sourcefoundry.org/hack/) is served together with the website. The favicons are generated by [favicon.io](https://favicon.io/).

See the [demo](https://piazzai.github.io/hacked-jekyll) to check the end result.

![](https://github.com/piazzai/hacked-jekyll/blob/master/screenshot.png)

## Installation

The theme can be installed as usual by cloning this repository and editing the files. However, it is far more convenient to install it as a gem, in which case all the files you do not want or need to customize remain hidden from view, but will still be read and processed during build.

To install the theme as a gem, you can then add this line to your `Gemfile`:

```ruby
gem "hacked-jekyll"
```

And this line to `_config.yml`:

```yaml
theme: hacked-jekyll
```

The easiest way to set up a new website in this way is to clone the contents of the `demo` folder. This provides a working set of files to get you started.

After you are done creating the basic files, run bundler:

    $ bundle

Or install the gem yourself as:

    $ gem install hacked-jekyll

To customize hidden files, you can create new files with the same names and paths. For example, to change the layout of the index page, you can create a `_layouts` folder and a file `index.html` within this folder that contains your custom code. During build, Jekyll will give priority to your files over the theme's.

## Usage

You can input the content of your JSON object in `_data/json.yml`. This is a list of key-value pairs: for each of them you need to provide `key` and `value`, as in the example below.

```yaml
- key: Name
  value: Place Holder
```

In addition, you can provide a `url`, in which case the value is rendered as a hyperlink. Here is an example:

```yaml
- key: Source
  value: piazzai/hacked-jekyll
  url: https://github.com/piazzai/hacked-jekyll
```

If `value` is a single line of text, the resulting JSON element will be a string. If `value` includes multiple lines of text, as in the code below, the resulting JSON element will be an array.

```yaml
- key: Address
  value:
    - University of Jekyll
    - Department of Themes
    - 123 Main St, Anytown, USA
```

An array can also consist of hyperlinks. To achieve this, provide each line of `value` with its own `value` and `url`, like so:

```yaml
- key: Profiles
  value:
    - value: Instagram
      url: https://www.instagram.com
    - value: LinkedIn
      url: https://www.linkedin.com
```

Finally, it is possible to render `value` as a hash, which is a list of key-value pairs. This will happen automatically if the elements of `value` have their own `key` and `value` (and possibly a `url`).

```yaml
- key: Contact
  value:
    - key: Office
      value: Foobar Hall 1.23
    - key: Phone
      value: +1 234 567 890
    - key: Email
      value: username@domain.com
      url: "mailto:username@domain.com"
```

You can customize the appearance of the rendered JSON object using site variables. These have default values that can be overridden by specifying a new value in your `_config.yml` file.

| Variable       |       Default       | Purpose                                               |
| -------------- | :-----------------: | ----------------------------------------------------- |
| `lowercase`    |       `true`        | Set all keys and values to lowercase                  |
| `color_bg`     | `var(--oc-gray-9)`  | Set the background color                              |
| `color_punct`  | `var(--oc-green-9)` | Set the color of quote marks, commas, and parentheses |
| `color_keyval` | `var(--oc-green-4)` | Set the color of all keys and values                  |
| `color_hover`  | `var(--oc-green-5)` | Set the color of values on hover (if they are links)  |
| `show_quotes`  |       `true`        | Display quote marks around keys and values            |
| `show_commas`  |       `true`        | Display commas between key-value pairs                |
| `target`       |       `_self`       | Set the target tab/window of hyperlinks               |

All color defaults use the naming convention of the Open Color library ([read here](https://yeun.github.io/open-color/documents.html)). You can change them to any other color in the library, any base CSS color, or any three or six-digit hex color. For example:

```yaml
color_bg: var(--oc-indigo-8)
color_punct: black
color_keyval: '#fff'
color_hover: '#cc5de8'
```

If you use Open Color names, remember to wrap them in a CSS variable.

Customizing the CSS is possible by creating a file `_sass/_custom.scss`. You can use this both to define new styles or to overwrite the theme's defaults. The file will be automatically compiled during build.

## Bugs

If you find any problem using the theme, please [open an issue](https://github.com/piazzai/hacked-jekyll/issues).
