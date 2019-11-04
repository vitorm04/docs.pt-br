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
ms.openlocfilehash: a39d25f03583ab9020878b7a659bc99489231ff9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458892"
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
 Para obter a especificação completa, consulte [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
