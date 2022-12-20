# Principles of writing consistent, idiomatic CSS

# თანმიმდევრული, იდიომატური CSS-ის წერის პრინციპები

The following document outlines a reasonable style guide for CSS development.
These guidelines strongly encourage the use of existing, common, sensible
patterns. They should be adapted as needed to create your own style guide.

წინამდებარე დოკუმენტი წარმოადგენს CSS-ის სტილისტიკის ზოგად სახელმძღვანელოს.
მოცემული მითითებები ძლიერ წაახალისებს არსებული, ფართოდ გავრცელებული, გონივრული ნიმუშების გამოყენებას.
საჭიროებისამებრ, თქვენ მიერ უნდა მოხდეს მათი გადაკეთება, რათა შექმნათ თქვენი საკუთარი მიდგომები.

This is a living document and new ideas are always welcome. Please
contribute.

წინამდებარე დოკუმენტი მუდმივი განვითარების პროცესშია და ახალი იდეები ყოველთვის მისასალმებელია.
გთხოვთ, შეიტანეთ თქვენი წვლილი.


## Table of contents

## სარჩევი

1. [ზოგადი პრინციპები](#general-principles)
2. [ინტერვალი](#whitespace)
3. [კომენტარები](#comments)
4. [ფორმატი](#format)
5. [პრაქტიკული მაგალითი](#example)

[მადლობა](#acknowledgements)

[ლიცენზია](#license)


<a name="general-principles"></a>
## 1. General principles

## 1. ზოგადი პრინციპები

> "Part of being a good steward to a successful project is realizing that
> writing code for yourself is a Bad Idea™. If thousands of people are using
> your code, then write your code for maximum clarity, not your personal
> preference of how to get clever within the spec." - Idan Gazit

> „იმის გაცნობიერება, რომ კოდის საკუთარი თავისთვის წერა ცუდი იდეაა™, წარმატებული პროექტის
> კარგ განმკარგულებლად ყოფნის ნაწილია. თუკი ათასობით ადამიანი იყენებს თქვენს კოდს,
> დაწერეთ კოდი რაც შეიძლება ნათლად და ნუ გააკეთებთ რამეს მხოლოდ იმიტომ, რომ ენის
> სპეციფიკაცია ამის საშუალებას იძლევა.“ — აიდან გაზიტი

* Don't try to prematurely optimize your code; keep it readable and
  understandable.
* All code in any code-base should look like a single person typed it, even
  when many people are contributing to it.
* Strictly enforce the agreed-upon style.
* If in doubt when deciding upon a style use existing, common patterns.

* ნუ ეცდებით თქვენი კოდის წინასწარ ოპტიმიზირებას; შუუნარჩუნეთ მას წაკითხვადი და
  გასაგები სახე.
* ნებისმიერ პროექტში არსებული მთლიანი კოდი ისე უნდა გამოიყურებოდეს, თითქოს ერთმა ადამიანმა დაწერა,
  მაშინაც კი, როცა მის შექმნაში მრავალი ადამიანი იღებს მონაწილეობას.
* მკაცრად დაიცავით შეთანხმებული სტილი.
* თუ ეჭვი გეპარებათ შერჩეული სტილის სისწორეში, გამოიყენეთ არსებული, ფართოდ გავრცელებული მიდგომები.


<a name="whitespace"></a>
## 2. Whitespace

## 2. ინტერვალი

Only one style should exist across the entire source of your code-base. Always
be consistent in your use of whitespace. Use whitespace to improve
readability.

მთელი კოდის მასშტაბით მხოლოდ ერთი სტილი უნდა ვრცელდებოდეს. მუდამ იყავით თანმიმდევრული
ინტერვალის გამოყენებისას. გამოიყენეთ ინტერვალი წაკითხვადობის
გასაუმჯობესებლად.

* _Never_ mix spaces and tabs for indentation.
* Choose between soft indents (spaces) or real tabs. Stick to your choice
  without fail. (Preference: spaces)
* If using spaces, choose the number of characters used per indentation level.
  (Preference: 4 spaces)

* _არასოდეს_ აურიოთ ერთმანეთში ინტერვალები და ტაბულაციები.
* გააკეთეთ არჩევანი რბილ აბზაცებსა (ინტერვალები) და ნამდვილ ტაბულაციას შორის (სასურველია ინტერვალები)
  და დაიცავით თქვენი არჩევანი უშეცდომოდ.
* თუ ინტერვალებს იყენებთ, შეარჩიეთ სიმბოლოთა ფიქსირებული რაოდენობა ყოველი აბზაცისათვის
  (სასურველია 4 ინტერვალი).

Tip: configure your editor to "show invisibles" or to automatically remove
end-of-line whitespace.

რჩევა: მოახდინეთ თქვენი რედაქტორის კონფიგურირება ისე, რომ „გიჩვენოთ უხილავი სიმბოლოები“ ან
ავტომატურად წაშალოს [არასაჭირო] ინტერვალი ხაზის ბოლოში.

Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to
help maintain the basic whitespace conventions that have been agreed for your
code-base.

რჩევა: გამოიყენეთ [EditorConfig](http://editorconfig.org/) ფაილი (ან მისი ეკვივალენტი),
რომელიც დაგეხმარებათ შეინარჩუნოთ ინტერვალის ის ძირითადი კანონზომიერებები, რომლებიც თქვენი
კოდისთვის შეარჩიეთ.


<a name="comments"></a>
## 3. Comments

## 3. კომენტარები

Well commented code is extremely important. Take time to describe components,
how they work, their limitations, and the way they are constructed. Don't leave
others in the team guessing as to the purpose of uncommon or non-obvious
code.

კოდის სწორად კომენტირება უაღრესად მნიშვნელოვანია. დაუთმეთ დრო კომპონენტების აღწერას:
როგორ მუშაობენ, რა შეზღუდვები აქვთ და როგორ არიან აგებული.
ნუ ჩააგდებთ გუნდის სხვა წევრებს საგონებელში, დაადგინონ,
რა არის უჩვეულო ან ბუნდოვანი კოდის დანიშნულება.

Comment style should be simple and consistent within a single code base.

კომენტარების ჩაწერის სტილი უნდა იყოს მარტივი და ურთიერთშეთანხმებული მთელი პროექტის მასშტაბით.

* Place comments on a new line above their subject.
* Keep line-length to a sensible maximum, e.g., 80 columns.
* Make liberal use of comments to break CSS code into discrete sections.
* Use "sentence case" comments and consistent text indentation.

* განათავსეთ კომენტარები ახალ ხაზზე, აღსაწერი კოდის ფრაგმენტის ზემოთ.
* ეცადეთ ხაზის სიგრძე არ აღემატებოდეს გონივრულ მაქსიმუმს, მაგალითად, 80 სიმბოლოს.
* ნუ შეიზღუდავთ თავს კომენტარების გამოყენებისგან CSS-კოდის ცალკეულ განყოფილებებად დანაწევრებისთვის.
* კომენტარები ჩაწერეთ ჩვეულებრივი გრამატიკული წინადადებების სახით. წინადადების ჩაწერა დაიწყეთ დიდი ასოთი და საჭიროებისამებრ გამოყავით აბზაცები.

Tip: configure your editor to provide you with shortcuts to output agreed-upon
comment patterns.

რჩევა: მოახდინეთ თქვენი რედაქტორის კონფიგურირება ისე, რომ თავად რედაქტორმა შემოგთავაზოთ წინასწარ
განსაზღვრული შაბლონების გამოყენება კომენტარების ჩასაწერად.

Example:

მაგალითი:

```css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* ==========================================================================
   კომენტარის ბლოკი განყოფილებისათვის
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/* კომენტარის ბლოკი ქვეგანყოფილებისათვის
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

/**
 * მოკლე აღწერა Doxygen სტილის კომენტარის ფორმატით
 *
 * ვრცელი აღწერის პირველი წინადადება იწყება აქ და გრძელდება
 * ამ ხაზზე, საბოლოოდ კი მთავრდება აქ - პარაგრაფის ბოლოში.
 *
 * ვრცელი აღწერა იდეალური ვარიანტია მეტად დეტალური აღწერისა და
 * დოკუმენტაციის უზრუნველსაყოფად. ის შეიძლება შეიცავდეს HTML-ის მაგალითს, URL-ებს ან ნებისმიერ
 * სხვა ინფორმაციას, რომელიც საჭიროდ ან გამოსადეგად იქნება მიჩნეული.
 *
 * @tag ეს არის ტეგი სახელად „tag“
 *
 * TODO: ეს არის „todo“ განცხადება, რომელიც აღწერს მოგვიანებით აუცილებლად
 * შესასრულებელ ამოცანას. მისი ყოველი პარაგრაფი შედგება არაუმეტეს 80 სიმბოლოსგან
 * და 2-ინტერვალიანი აბზაცისგან.
 */

/* Basic comment */

/* მინიმალისტური კომენტარი */
```


<a name="format"></a>
## 4. Format

## 4. ფორმატი

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

თქვენ მიერ შერჩეული კოდის ჩაწერის ფორმატი უნდა იძლეოდეს გარანტიას, რომ კოდი არის
მარტივად წაკითხვადი, შედგება მარტივად გასაგები კომენტარებისგან, მინიმუმამდე ამცირებს
შეცდომების დაშვების შანსს და იძლევა გამოსადეგ შეტყობინებებს ვერსიების კონტროლის კონტექსტში.

* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* Use single or double quotes consistently. Preference is for double quotes,
  e.g., `content: ""`.
* Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Place the closing brace of a ruleset in the same column as the first
  character of the ruleset.
* Separate each ruleset by a blank line.

* რამდენიმე სელექტორისგან შემდგარი წესების ნაკრების ჩაწერისას, ყოველი ცალკეული სელექტორი განათავსეთ ცალკე ხაზზე.
* წესების ნაკრების გამხსნელი ფიგურული ფრჩხილის წინ განათავსეთ ერთი ინტერვალი.
* დეკლარაციათა ბლოკში შემავალი ყოველი დეკლარაცია განათავსეთ ცალკე ხაზზე.
* თითოეული დეკლარაციისთვის გამოიყენეთ ერთდონიანი აბზაცი (_ერთი ტაბი_).
* დეკლარაციაში, ორწერტილის შემდეგ განათავსეთ ერთი ინტერვალი.
* გამოიყენეთ პატარა ასოებით ჩაწერილი შემოკლებული თექვსმეტობითი მნიშვნელობები. მაგალითად: `#aaa`.
* მუდმივად გამოიყენეთ ერთმაგი ან ორმაგი ბრჭყალები (_ნუ მოახდენთ მათ შერევას_). სასურველია ორმაგი ბრჭყალების გამოყენება,
  მაგალითად: `content: ""`.
* სელექტორებში, ატრიბუტების მნიშვნელობები ჩასვით ბრჭყალებში. მაგალითად: `input[type="checkbox"]`.
* _დასაშვებ შემთხვევებში_, მოერიდეთ ნულოვანი მნიშვნელობებისათვის ერთეულების განსაზღვრას. მაგალითად: `margin: 0`.
* მძიმით გამოყოფილ თვისებათა ან ფუნქციათა მნიშვნელობებში,
  ყოველი მძიმის შემდეგ განათავსეთ ერთი ინტერვალი.
* დეკლარაციათა ბლოკის უკანასკნელი დეკლარაციის ბოლოში(_ც_) განათავსეთ
  წერტილ-მძიმე.
* წესების ნაკრების დამხურავი ფრჩხილი განათავსეთ იმავე სვეტზე, რომელზედაც წესების ნაკრების პირველი
  სიმბოლოა განთავსებული.
* გამოყავით წესების თითოეული ნაკრები ცარიელი ხაზით.

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
    padding: 10px;
}
```

#### Declaration order

#### დეკლარაციათა თანმიმდევრობა

If declarations are to be consistently ordered, it should be in accordance with
a single, simple principle.

თუ დეკლარაციების თანმიმდევრობით დალაგებაა საჭირო, ეს უნდა მოხდეს ერთი მარტივი
პრინციპის შესაბამისად.

Smaller teams may prefer to cluster related properties (e.g. positioning and
box-model) together.

შედარებით პატარა გუნდებმა შესაძლოა უპირატესობა მიანიჭონ ურთიერთდაკავშირებულ თვისებათა (მაგ. პოზიციონირება და ბლოკის მოდელი (_box-model_)) ერთად თავმოყრას.

```css
.selector {
    /* Positioning */

    /* პოზიციონირება */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Display & Box Model */

    /* ვიზუალიზაცია (Display) და ბლოკის მოდელი */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Other */

    /* სხვა */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Larger teams may prefer the simplicity and ease-of-maintenance that comes with
alphabetical ordering.

უფრო დიდმა გუნდებმა კი შესაძლოა სიმარტივესა და მოხერხებულად მოვლის შესაძლებლობაზე გააკეთონ არჩევანი,
რაც ანბანური თანმიმდევრობით დალაგების პრინციპისთვის არის დამახასიათებელი.

#### Exceptions and slight deviations

#### გამონაკლისები და მცირედი გადახვევები

Large blocks of single declarations can use a slightly different, single-line
format. In this case, a space should be included after the opening brace and
before the closing brace.

ერთი დეკლარაციისგან შემდგარი დიდი ბლოკებისთვის შეიძლება გამოყენებულ იქნეს ოდნავ განსხვავებული, ერთხაზიანი
ფორმატი. ამ შემთხვევაში, ინტერვალი გამხსნელი ფრჩხილის შემდეგ და დამხურავი ფრჩხილის წინ უნდა
განთავსდეს.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Long, comma-separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs. There are various formats that could
be used; one example is shown below.

გრძელი, მძიმით გამოყოფილი თვისებათა მნიშვნელობები — როგორიცაა გრადიენტთა ან ჩრდილთა
კრებული — შეიძლება განლაგებულ იქნეს მრავალ სტრიქონზე, რათა გაუმჯობესდეს
წაკითხვადობა და წარმოიქმნას მეტად გამოსადეგი diff-ები. არსებობს სხვადასხვა ჩაწერის ფორმატები;
ერთ-ერთი ვარიანტი ქვემოთ არის მოცემული.

```css
.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Preprocessors: additional format considerations

### პრეპროცესორები: დამატებითი მოსაზრებები ფორმატის თაობაზე

Different CSS preprocessors have different features, functionality, and syntax.
Your conventions should be extended to accommodate the particularities of any
preprocessor in use. The following guidelines are in reference to Sass.

სხვადასხვა CSS-პრეპროცესორს განსხვავებული ფუნქციონალი და სინტაქსი აქვს.
თქვენი მიდგომები უნდა მოერგოს თქენ მიერ გამოყენებული ამა თუ იმ პრეპროცესორის
თავისებურებებს. ქვემოთ მოცემული მითითებები Sass-ზე ვრცელდება.

* Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep.
  This prevents overly-specific CSS selectors.
* Avoid large numbers of nested rules. Break them up when readability starts to
  be affected. Preference to avoid nesting that spreads over more than 20
  lines.
* Always place `@extend` statements on the first lines of a declaration
  block.
* Where possible, group `@include` statements at the top of a declaration
  block, after any `@extend` statements.
* Consider prefixing custom functions with `x-` or another namespace. This
  helps to avoid any potential to confuse your function with a native CSS
  function, or to clash with functions from libraries.

* შეზღუდეთ (სელექტორთა) ჩადგმის სიღრმე ერთამდე. მოახდინეთ კოდის ნებისმიერი ფრაგმენტის გადაფასება,
  სადაც ჩადგმის სიღრმე ერთს აღემატება. ეს ზედმეტად სპეციფიკური CSS-სელექტორების აღმოფხვრას შეუწყობს ხელს.
* მოერიდეთ ჩადგმული წესის დეკლარაციების დიდი რაოდენობით გამოყენებას. როგორც კი შეატყობთ,
  რომ ისინი წაკითხვადობაზე ცუდად ზემოქმედებენ, დაყავით ისინი პატარა, ლოგიკურ ფრაგმენტებად.
  უმჯობესია, ჩადგმული კოდი ვრცელდებოდეს არაუმეტეს 20 ხაზის მასშტაბით.
* `@extend` განცხადებები ყოველთვის განათავსეთ დეკლარაციის ბლოკის პირველ
  ხაზებში.
* სადაც ამის შესაძლებლობა გექნებათ, `@include` განცხადებებს თავი მოუყარეთ დეკლარაციის ბლოკის პირველ ხაზებში,
  `@extend` განცხადებების შემდეგ.
* განიხილეთ თქვენ მიერ შექმნილი (_custom_) ფუნქციებისათვის `x-` ან სხვა _namespace_-ის დამატება თავსართის სახით.
  ეს დაგეხმარებათ თავიდან აირიდოთ ყველანაირი შესაძლებლობა იმისა, რომ თქვენ მიერ შექმნილ და CSS-ში ჩაშენებულ ფუნქციებს შორის, —
  ასევე თქვენ მიერ შექმნილ და ბიბლიოთეკების მიერ უზრუნველყოფილ ფუნქციებს შორის, — მოხდება კონფლიქტი.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations

    // სხვა დეკლარაციები
}
```


<a name="example"></a>
## 5. Practical example

## 5. პრაქტიკული მაგალითი

An example of various conventions.

რამდენიმე კანონზომიერების მაგალითი.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/* ==========================================================================
   Grid-აგებულება
   ========================================================================== */

/**
 * Column layout with horizontal scroll.
 *
 * This creates a single row of full-height, non-wrapping columns that can
 * be browsed horizontally within their parent.
 *
 * Example HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * ჰორიზონტალური სქროლის მქონე სვეტის აგებულება.
 *
 * იქმნება სრული სიმაღლის მქონე, შეუფუთავი სვეტების ერთი რიგი,
 * რომელთა დათვალიერებაც შესაძლებელია ჰორიზონტალურად, კონტეინერის
 * (ანუ მშობელი ელემენტის) შიგნით.
 *
 * HTML-ის ნიმუში:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Grid container
 *
 * Must only contain `.cell` children.
 *
 * 1. Remove inter-cell whitespace
 * 2. Prevent inline-block cells wrapping
 */

/**
 * Grid-კონტეინერი:
 *
 * უნდა შეიცავდეს მხოლოდ `.cell` შვილობილ ელემენტებს.
 *
 * 1. უჯრედთაშორისი სივრცის მოცილება
 * 2. მწკრივულ უჯრედთა ბლოკის შეფუთვის აღმოფხვრა
 */

.grid {
    height: 100%;
    font-size: 0; /* 1 */
    white-space: nowrap; /* 2 */
}

/**
 * Grid cells
 *
 * No explicit width by default. Extend with `.cell-n` classes.
 *
 * 1. Set the inter-cell spacing
 * 2. Reset white-space inherited from `.grid`
 * 3. Reset font-size inherited from `.grid`
 */

/**
 * Grid-უჯრედები
 *
 * ნაგულისხმევად, ზუსტი სიგანე არ არის განსაზღვრული. გავრცობილია `.cell-n` კლასებით.
 *
 * 1. უჯრედთაშორისი ინტერვალის განსაზღვრა
 * 2. `.grid`-ისგან მემკვიდრეობით მიღებული white-space თვისების ხელახლა განსაზღვრა
 * 3. `.grid`-ისგან მემკვიდრეობით მიღებული font-size თვისების ხელახლა განსაზღვრა
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    padding: 0 10px; /* 1 */
    border: 2px solid #333;
    vertical-align: top;
    white-space: normal; /* 2 */
    font-size: 16px; /* 3 */
}

/* Cell states */

/* უჯრედთა მდგომარეობები/ვარიაციები */

.cell.is-animating {
    background-color: #fffdec;
}

/* Cell dimensions
   ========================================================================== */

/* უჯრედთა ზომები
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ========================================================================== */

/* უჯრედთა მოდიფიკატორები
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="acknowledgements"></a>
## Acknowledgements

## მადლობა

Thanks to everyone who has provided translations and to all those who
contributed to [idiomatic.js](https://github.com/rwldrn/idiomatic.js). It was a
source of inspiration, quotations, and guidelines.

მადლობა ყველას, ვინც მონაწილეობა მიიღო თარგმანების შემუშავების პროცესში,
ასევე ყველა იმ ადამიანს, ვინც წვლილი შეიტანა [idiomatic.js](https://github.com/rwldrn/idiomatic.js)-ის
შედგენაში. სწორედ ეს გახლდათ შთაგონების, ციტატებისა და სახელმძღვანელო მითითებების წყარო.
