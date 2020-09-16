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
ms.openlocfilehash: ceb027938b6d4313babbe02949e0b6dd5ee85589
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556688"
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

| Categoria Unicode   | Description                   |
|--------------------|-------------------------------|
| Lu                 | Letra, maiúscula             |
| LI                 | Letra, minúscula             |
| Lt                 | Letra, título             |
| Lm                 | Letra, modificador              |
| Lo                 | Letra, outra                 |
| Mn                 | Marcar, sem espaçamento             |
| MC                 | Marca, combinação de espaçamento       |
| Nd                 | Número, decimal               |
| NL                 | Número, letra                |

O XAML define uma segunda gramática, DottedXamlName, usada para referências qualificadas de propriedade e evento e também para membros anexados. Para obter mais informações, consulte <xref:System.Windows.DependencyProperty> e [visão geral do XAML (WPF)](../fundamentals/xaml.md).

Os valores de cadeia de caracteres do tipo DottedXamlName devem estar de acordo com a gramática a seguir:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Comentários

Para obter a especificação completa, consulte [ \[ MS- \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10)).
