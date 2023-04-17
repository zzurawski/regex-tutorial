# RegEX How-to-Match-HTML

This gist is a tutorial on how to match an HTML tag using regular expression

## Summary
Matching HTML tags with regular expression can be a bit complex because of the various tag variations. But by identifying common patterns and writing a regular expression, we can match HTML tags in a string of HTML code.

## How to First Approach
If you are uncomfortable with HTML, a tag is composed of a specific key closed within a <>. <> marks the beginning of the content placed within the tag and </> marks the end of said content. Other markings in the tags can be attributes which are displayed by double quotes and are separated by an equals sign.

## Getting Comfortable with RegEx
A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

## RegEx Symbols
RegEx utilizes ([a-zA-Z]+) to match alphabetical characters (upper and lowercase) as there are no numerical tags. With [^>]* matches all the other characters in the tag that are not the > symbol. 

## How to Match the HTML Tag 
If beginning tag, "<([a-zA-Z]+)[^>]*>"
If the end tag,   "</([a-zA-Z]+)[^>]*>"

## Code Snippet
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class HtmlTagMatcher {
    public static void main(String[] args) {
        String html = "<html><head><title>Example</title></head><body><p>This is a paragraph.</p></body></html>";
        Pattern pattern = Pattern.compile("<([a-zA-Z]+)[^>]*>");
        Matcher matcher = pattern.matcher(html);
        while (matcher.find()) {
            System.out.println(matcher.group());
        }
    }
}