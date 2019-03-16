---
title: Gramática XamlName
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 642ca16142bdfe78a40ddf4e6a3a79ce6a8a4985
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031607"
---
# <a name="xamlname-grammar"></a>Gramática XamlName
Gramática XamlName é uma gramática específica que é definida na especificação de linguagem XAML [MS-XAML], que é reproduzida aqui para sua conveniência.  
  
## <a name="from-the-xaml-specification"></a>Da especificação XAML  
 A especificação [MS-XAML] define a gramática XamlName para identificar o conjunto de identificadores simbólicos legais utilizados para tipos e propriedades.  
  
 Cadeia de caracteres valores que são do tipo XamlName deve estar de acordo com a gramática a seguir:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Que pressupõe os seguintes valores de categoria geral, conforme definido no banco de dados de caractere Unicode  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML define uma segunda gramática, DottedXamlName, que é usado para a propriedade e evento referências qualificadas e também membros anexos. Para obter mais informações, consulte <xref:System.Windows.DependencyProperty> e [visão geral de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md).  
  
 Cadeia de caracteres valores que são do tipo XamlName deve estar de acordo com a gramática a seguir:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Comentários  
 Para a especificação completa, consulte [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
