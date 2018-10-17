---
title: html-dom-node-type
date: 2018-10-17 19:38:34
tags:
---


| const                             | value | desc                                          |
|-----------------------------------|-------|-----------------------------------------------| 
| Node.ELEMENT_NODE                 | 1     | Element(node)                                 |
| Node.ATTRIBUTE_NODE               | 2     | Attr(deprecated)                              |
| Node.TEXT_NODE                    | 3     | Text for Element of Attr                      |
| Node.CDATA_SECTION_NODE           | 4     | CDATASection                                  |
| Node.ENTITY_REFERENCE_NODE        | 5     | XML<!ENTITY ...>(node)(deprecated)            |
| Node.ENTITY_NODE                  | 6     | XML<!ENTITY ...>(node)(deprecated)            |
| Node.PROCESSING_INSTRUCTION_NODE  | 7     | ProcessingInstruction <?xml-stylesheet ... ?> |
| Node.COMMENT_NODE                 | 8     | Comment(node)                                 |
| Node.DOCUMENT_NODE                | 9     | Document(node)                                |
| Node.DOCUMENT_TYPE_NODE	        | 10    | DocumentType(node) eg: <!DOCTYPE html>        |
| Node.DOCUMENT_FRAGMENT_NODE       | 11    | DocumentFragment(node)                        |
| Node.NOTATION_NODE	            | 12    | XML <!NOTATION ...>(node)(deprecated)         |

`2,5,6,12`, `ATTRIBUTE_NODE, ENTITY_REFERENCE_NODE, ENTITY_NODE, NOTATION_NODE` have `deprecated`