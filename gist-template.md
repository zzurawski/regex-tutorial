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

## Regex Terminology

## Table of Contents
    [Anchors](#anchors)
    [Brackets](#bracket-expression)
    [Quantifiers](#quantifiers)
    [Grouping](#grouping)
    [OR](#or)
    [Escape/Classes](#character-escapes/classes)
    
## Anchors
"^" marks a string that begins with the available characters that follow it. "$" marks a string that ends with the designated characters that precede it.

## Bracket Expression
Brackets mark the range of characters the expression needs to match. Hyphens in the brackets means it encompasses all in between the two expressions on either side (a-z means all lowercase alphabetical, 0-9 means all numbers). If a carrot is added to the beginning, its means it cannot match those values.

## Quantifiers
These set the limit of characters for the matched string. 
Items:
    * = matches >=0
    + = matches >=1
    ? =matches 0 or 1
Curly brackets can either mark exact amount of times, marks a minimum, or marks both min and max

## Grouping 
Parantheses within the parent parantheses mark subexpressions which can mark different parts of strings to match. These can be also used for capturing and non-capturing.

## OR
Marked by a "|", the OR operator shows us different characters that can be included in a non-specific order or grouping.

## Character Escape/Classes
Escape:
    Commonly used for special characters, this method is marked with a backslash "\". Thus, the method is not read literally and can be included in the match.
Classes:
    Shorthand marks to define matchable characteristics,
        "." = any character except newline
        "\d" = any arabic numeral (0-9)
        "\w" = matches alphanumerical characters including _
        "\s" = matches blankspace characters for line breaks and tabs
