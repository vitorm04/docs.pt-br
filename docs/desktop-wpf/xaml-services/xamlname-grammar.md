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
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071825"
---
# <a name="xamlname-grammar"></a>Gramática XamlName

XamlName Grammar é uma gramática específica que é definida na especificação da linguagem XAML [MS-XAML], que é reproduzida aqui por conveniência.

## <a name="from-the-xaml-specification"></a>A partir da especificação XAML

A especificação [MS-XAML] define a gramática XamlName para identificar o conjunto de identificadores simbólicos legais usados para tipos e propriedades.

Os valores de string que são do tipo XamlName devem estar em conformidade com a seguinte gramática:

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

Que assume os seguintes valores gerais da categoria conforme definido no Banco de Dados de Caracteres Unicode

| Categoria Unicode   | Descrição                   |
|--------------------|-------------------------------|
| Lu                 | Letra, maiúscula             |
| LI                 | Letra, minúscula             |
| Lt                 | Letra, título             |
| Lm                 | Letra, modificador              |
| Lo                 | Letra, outra                 |
| Mn                 | Mark, Não-Espaçamento             |
| MC                 | Marca, combinação de espaçamento       |
| Nd                 | Número, Decimal               |
| NL                 | Número, letra                |

XAML define uma segunda gramática, DottedXamlName, que é usada para referências qualificadas de propriedade e eventos, e também para membros anexados. Para obter mais <xref:System.Windows.DependencyProperty> informações, consulte e [XAML Overview (WPF)](../fundamentals/xaml.md).

Os valores de string que são do tipo DottedXamlName devem estar em conformidade com a seguinte gramática:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Comentários

Para obter a especificação completa, consulte [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
