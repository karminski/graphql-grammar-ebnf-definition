Graphql 语法 EBNF 定义
----------------------

根据 June 2018 版本的 GraphQL 语法定义转写的 EBNF 定义.   
创建该 repo 的目的是更方便地编写 GraphQL Parser 和 Lexer.  

# EBNF

## 预览:  

```EBNF
/* SourceCharacter Expression */
SourceCharacter ::=  #x0009 | #x000A | #x000D | [#x0020-#xFFFF] /* /[\u0009\u000A\u000D\u0020-\uFFFF]/ */
/* Ignored Tokens Expression */
Ignored        ::= UnicodeBOM | WhiteSpace | LineTerminator | Comment | Comma
UnicodeBOM     ::= #xFEFF  /* Byte Order Mark (U+FEFF) */
WhiteSpace     ::= #x0009 | #x0020 /* ASCII: \t | Space, Horizontal Tab (U+0009), Space (U+0020) */
LineTerminator ::= #x000A | #x000D | #x000D#x000A   /* ASCII: \n | \r\n | \r, New Line (U+000A) | Carriage Return (U+000D) [Lookahead != New Line (U+000A)] | Carriage Return (U+000D)New Line (U+000A) */
Comment        ::= "#" CommentChar* LineTerminator
CommentChar    ::= SourceCharacter - LineTerminator
Comma          ::= ","

...
```

## 详情:
-  [GraphQL-Grammar-EBNF-Definition-June-2018-Edition](./DOCUMENTS/June-2018-Edition/GraphQL-Grammar-EBNF-Definition-June-2018-Edition.ebnf)  



# 语法图 (铁路图)

## 预览 (通过 [Railroad Diagram Generator](https://bottlecaps.de/rr/ui) 生成):  

<p xmlns:xhtml="http://www.w3.org/1999/xhtml" style="font-size: 14px; font-weight:bold">
    <b>SourceCharacter:</b>
</p>
<svg xmlns="http://www.w3.org/2000/svg" width="239" height="169">
         <defs>
            <style type="text/css">
    @namespace "http://www.w3.org/2000/svg";
    .line                 {fill: none; stroke: #332900; stroke-width: 1;}
    .bold-line            {stroke: #141000; shape-rendering: crispEdges; stroke-width: 2;}
    .thin-line            {stroke: #1F1800; shape-rendering: crispEdges}
    .filled               {fill: #332900; stroke: none;}
    text.terminal         {font-family: Verdana, Sans-serif;
                            font-size: 12px;
                            fill: #141000;
                            font-weight: bold;
                          }
    text.nonterminal      {font-family: Verdana, Sans-serif;
                            font-size: 12px;
                            fill: #1A1400;
                            font-weight: normal;
                          }
    text.regexp           {font-family: Verdana, Sans-serif;
                            font-size: 12px;
                            fill: #1F1800;
                            font-weight: normal;
                          }
    rect, circle, polygon {fill: #332900; stroke: #332900;}
    rect.terminal         {fill: #FFDB4D; stroke: #332900; stroke-width: 1;}
    rect.nonterminal      {fill: #FFEC9E; stroke: #332900; stroke-width: 1;}
    rect.text             {fill: none; stroke: none;}
    polygon.regexp        {fill: #FFF4C7; stroke: #332900; stroke-width: 1;}
  </style>
         </defs>
         <polygon points="9 17 1 13 1 21"/>
         <polygon points="17 17 9 13 9 21"/>
         <polygon points="51 19 58 3 134 3 141 19 134 35 58 35"/>
         <polygon points="49 17 56 1 132 1 139 17 132 33 56 33" class="regexp"/>
         <text class="regexp" x="64" y="21">[#x0009]</text>
         <polygon points="51 63 58 47 134 47 141 63 134 79 58 79"/>
         <polygon points="49 61 56 45 132 45 139 61 132 77 56 77" class="regexp"/>
         <text class="regexp" x="64" y="65">[#x000A]</text>
         <polygon points="51 107 58 91 134 91 141 107 134 123 58 123"/>
         <polygon points="49 105 56 89 132 89 139 105 132 121 56 121" class="regexp"/>
         <text class="regexp" x="64" y="109">[#x000D]</text>
         <polygon points="51 151 58 135 184 135 191 151 184 167 58 167"/>
         <polygon points="49 149 56 133 182 133 189 149 182 165 56 165" class="regexp"/>
         <text class="regexp" x="64" y="153">[#x0020-#xFFFF]</text>
         <path xmlns:svg="http://www.w3.org/2000/svg" class="line" d="m17 17 h2 m20 0 h10 m90 0 h10 m0 0 h50 m-180 0 h20 m160 0 h20 m-200 0 q10 0 10 10 m180 0 q0 -10 10 -10 m-190 10 v24 m180 0 v-24 m-180 24 q0 10 10 10 m160 0 q10 0 10 -10 m-170 10 h10 m90 0 h10 m0 0 h50 m-170 -10 v20 m180 0 v-20 m-180 20 v24 m180 0 v-24 m-180 24 q0 10 10 10 m160 0 q10 0 10 -10 m-170 10 h10 m90 0 h10 m0 0 h50 m-170 -10 v20 m180 0 v-20 m-180 20 v24 m180 0 v-24 m-180 24 q0 10 10 10 m160 0 q10 0 10 -10 m-170 10 h10 m140 0 h10 m23 -132 h-3"/>
         <polygon points="229 17 237 13 237 21"/>
         <polygon points="229 17 221 13 221 21"/>
</svg>
         
<p xmlns:xhtml="http://www.w3.org/1999/xhtml">
    <div class="ebnf">
        <code>
            <div><b>SourceCharacter</b></div>
            <div>         ::= [#x0009#x000A#x000D#x0020-#xFFFF]</div>
        </code>
    </div>
</p>
<p>referenced by:
   <ul>
      <li><b>BlockStringCharacter</b></li>
      <li><b>CommentChar</b></li>
      <li><b>StringCharacter</b></li>
   </ul>
</p>

## 详情:
- [GraphQL-Grammar-Diagram-June-2018-Edition](./DOCUMENTS/June-2018-Edition/GraphQL-Grammar-Diagram-June-2018-Edition.xhtml)

# 作者
- karminski

# 协议
- MIT