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
ms.openlocfilehash: a1e7a5a03db4a24ed4d13d62899754cfe9e76b56
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837149"
---
# <a name="xamlname-grammar"></a>Gramática XamlName
XamlName gramática é uma gramática específica que é definida na especificação da linguagem XAML [MS-XAML], que é reproduzida aqui para sua conveniência.  
  
## <a name="from-the-xaml-specification"></a>Da especificação XAML  
 A especificação [MS-XAML] define a Gramática XamlName para identificar o conjunto de identificadores simbólicos legais usado para tipos e propriedades.  
  
 Os valores de cadeia de caracteres do tipo XamlName devem estar de acordo com a gramática a seguir:  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Que assume os seguintes valores gerais de categoria, conforme definido no banco de dados de caracteres Unicode  

| Categoria Unicode   | Descrição                   |
|--------------------|-------------------------------|
| Lu                 | Letra, maiúscula             |
| LI                 | Letra, minúscula             |
| Lt                 | Letra, título             |
| Lm                 | Letra, modificador              |
| Lo                 | Letra, outra                 |
| Mn                 | Marcar, sem espaçamento             |
| MC                 | Marca, combinação de espaçamento       |
| Nd                 | Número, decimal               |
| Nl                 | Número, letra                |
 
 O XAML define uma segunda gramática, DottedXamlName, usada para referências qualificadas de propriedade e evento e também para membros anexados. Para obter mais informações, consulte Visão geral de <xref:System.Windows.DependencyProperty> e [XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).  
  
 Os valores de cadeia de caracteres do tipo DottedXamlName devem estar de acordo com a gramática a seguir:  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Comentários  
 Para obter a especificação completa, consulte [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
