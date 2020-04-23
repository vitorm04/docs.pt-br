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
# <a name="xamlname-grammar"></a><span data-ttu-id="a57ab-102">Gramática XamlName</span><span class="sxs-lookup"><span data-stu-id="a57ab-102">XamlName Grammar</span></span>

<span data-ttu-id="a57ab-103">XamlName Grammar é uma gramática específica que é definida na especificação da linguagem XAML [MS-XAML], que é reproduzida aqui por conveniência.</span><span class="sxs-lookup"><span data-stu-id="a57ab-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="a57ab-104">A partir da especificação XAML</span><span class="sxs-lookup"><span data-stu-id="a57ab-104">From the XAML Specification</span></span>

<span data-ttu-id="a57ab-105">A especificação [MS-XAML] define a gramática XamlName para identificar o conjunto de identificadores simbólicos legais usados para tipos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="a57ab-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="a57ab-106">Os valores de string que são do tipo XamlName devem estar em conformidade com a seguinte gramática:</span><span class="sxs-lookup"><span data-stu-id="a57ab-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="a57ab-107">Que assume os seguintes valores gerais da categoria conforme definido no Banco de Dados de Caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="a57ab-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="a57ab-108">Categoria Unicode</span><span class="sxs-lookup"><span data-stu-id="a57ab-108">Unicode category</span></span>   | <span data-ttu-id="a57ab-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a57ab-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="a57ab-110">Lu</span><span class="sxs-lookup"><span data-stu-id="a57ab-110">Lu</span></span>                 | <span data-ttu-id="a57ab-111">Letra, maiúscula</span><span class="sxs-lookup"><span data-stu-id="a57ab-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="a57ab-112">LI</span><span class="sxs-lookup"><span data-stu-id="a57ab-112">Ll</span></span>                 | <span data-ttu-id="a57ab-113">Letra, minúscula</span><span class="sxs-lookup"><span data-stu-id="a57ab-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="a57ab-114">Lt</span><span class="sxs-lookup"><span data-stu-id="a57ab-114">Lt</span></span>                 | <span data-ttu-id="a57ab-115">Letra, título</span><span class="sxs-lookup"><span data-stu-id="a57ab-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="a57ab-116">Lm</span><span class="sxs-lookup"><span data-stu-id="a57ab-116">Lm</span></span>                 | <span data-ttu-id="a57ab-117">Letra, modificador</span><span class="sxs-lookup"><span data-stu-id="a57ab-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="a57ab-118">Lo</span><span class="sxs-lookup"><span data-stu-id="a57ab-118">Lo</span></span>                 | <span data-ttu-id="a57ab-119">Letra, outra</span><span class="sxs-lookup"><span data-stu-id="a57ab-119">Letter, Other</span></span>                 |
| <span data-ttu-id="a57ab-120">Mn</span><span class="sxs-lookup"><span data-stu-id="a57ab-120">Mn</span></span>                 | <span data-ttu-id="a57ab-121">Mark, Não-Espaçamento</span><span class="sxs-lookup"><span data-stu-id="a57ab-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="a57ab-122">MC</span><span class="sxs-lookup"><span data-stu-id="a57ab-122">Mc</span></span>                 | <span data-ttu-id="a57ab-123">Marca, combinação de espaçamento</span><span class="sxs-lookup"><span data-stu-id="a57ab-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="a57ab-124">Nd</span><span class="sxs-lookup"><span data-stu-id="a57ab-124">Nd</span></span>                 | <span data-ttu-id="a57ab-125">Número, Decimal</span><span class="sxs-lookup"><span data-stu-id="a57ab-125">Number, Decimal</span></span>               |
| <span data-ttu-id="a57ab-126">NL</span><span class="sxs-lookup"><span data-stu-id="a57ab-126">Nl</span></span>                 | <span data-ttu-id="a57ab-127">Número, letra</span><span class="sxs-lookup"><span data-stu-id="a57ab-127">Number, Letter</span></span>                |

<span data-ttu-id="a57ab-128">XAML define uma segunda gramática, DottedXamlName, que é usada para referências qualificadas de propriedade e eventos, e também para membros anexados.</span><span class="sxs-lookup"><span data-stu-id="a57ab-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="a57ab-129">Para obter mais <xref:System.Windows.DependencyProperty> informações, consulte e [XAML Overview (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a57ab-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="a57ab-130">Os valores de string que são do tipo DottedXamlName devem estar em conformidade com a seguinte gramática:</span><span class="sxs-lookup"><span data-stu-id="a57ab-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="a57ab-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a57ab-131">Remarks</span></span>

<span data-ttu-id="a57ab-132">Para obter a especificação completa, consulte [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="a57ab-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
