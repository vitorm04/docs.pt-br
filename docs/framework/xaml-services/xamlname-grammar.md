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
# <a name="xamlname-grammar"></a><span data-ttu-id="4107c-102">Gramática XamlName</span><span class="sxs-lookup"><span data-stu-id="4107c-102">XamlName Grammar</span></span>
<span data-ttu-id="4107c-103">XamlName gramática é uma gramática específica que é definida na especificação da linguagem XAML [MS-XAML], que é reproduzida aqui para sua conveniência.</span><span class="sxs-lookup"><span data-stu-id="4107c-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="4107c-104">Da especificação XAML</span><span class="sxs-lookup"><span data-stu-id="4107c-104">From the XAML Specification</span></span>  
 <span data-ttu-id="4107c-105">A especificação [MS-XAML] define a Gramática XamlName para identificar o conjunto de identificadores simbólicos legais usado para tipos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="4107c-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="4107c-106">Os valores de cadeia de caracteres do tipo XamlName devem estar de acordo com a gramática a seguir:</span><span class="sxs-lookup"><span data-stu-id="4107c-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="4107c-107">Que assume os seguintes valores gerais de categoria, conforme definido no banco de dados de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="4107c-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="4107c-108">Categoria Unicode</span><span class="sxs-lookup"><span data-stu-id="4107c-108">Unicode category</span></span>   | <span data-ttu-id="4107c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4107c-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="4107c-110">Lu</span><span class="sxs-lookup"><span data-stu-id="4107c-110">Lu</span></span>                 | <span data-ttu-id="4107c-111">Letra, maiúscula</span><span class="sxs-lookup"><span data-stu-id="4107c-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="4107c-112">LI</span><span class="sxs-lookup"><span data-stu-id="4107c-112">Ll</span></span>                 | <span data-ttu-id="4107c-113">Letra, minúscula</span><span class="sxs-lookup"><span data-stu-id="4107c-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="4107c-114">Lt</span><span class="sxs-lookup"><span data-stu-id="4107c-114">Lt</span></span>                 | <span data-ttu-id="4107c-115">Letra, título</span><span class="sxs-lookup"><span data-stu-id="4107c-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="4107c-116">Lm</span><span class="sxs-lookup"><span data-stu-id="4107c-116">Lm</span></span>                 | <span data-ttu-id="4107c-117">Letra, modificador</span><span class="sxs-lookup"><span data-stu-id="4107c-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="4107c-118">Lo</span><span class="sxs-lookup"><span data-stu-id="4107c-118">Lo</span></span>                 | <span data-ttu-id="4107c-119">Letra, outra</span><span class="sxs-lookup"><span data-stu-id="4107c-119">Letter, Other</span></span>                 |
| <span data-ttu-id="4107c-120">Mn</span><span class="sxs-lookup"><span data-stu-id="4107c-120">Mn</span></span>                 | <span data-ttu-id="4107c-121">Marcar, sem espaçamento</span><span class="sxs-lookup"><span data-stu-id="4107c-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="4107c-122">MC</span><span class="sxs-lookup"><span data-stu-id="4107c-122">Mc</span></span>                 | <span data-ttu-id="4107c-123">Marca, combinação de espaçamento</span><span class="sxs-lookup"><span data-stu-id="4107c-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="4107c-124">Nd</span><span class="sxs-lookup"><span data-stu-id="4107c-124">Nd</span></span>                 | <span data-ttu-id="4107c-125">Número, decimal</span><span class="sxs-lookup"><span data-stu-id="4107c-125">Number, Decimal</span></span>               |
| <span data-ttu-id="4107c-126">Nl</span><span class="sxs-lookup"><span data-stu-id="4107c-126">Nl</span></span>                 | <span data-ttu-id="4107c-127">Número, letra</span><span class="sxs-lookup"><span data-stu-id="4107c-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="4107c-128">O XAML define uma segunda gramática, DottedXamlName, usada para referências qualificadas de propriedade e evento e também para membros anexados.</span><span class="sxs-lookup"><span data-stu-id="4107c-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="4107c-129">Para obter mais informações, consulte Visão geral de <xref:System.Windows.DependencyProperty> e [XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4107c-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="4107c-130">Os valores de cadeia de caracteres do tipo DottedXamlName devem estar de acordo com a gramática a seguir:</span><span class="sxs-lookup"><span data-stu-id="4107c-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="4107c-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="4107c-131">Remarks</span></span>  
 <span data-ttu-id="4107c-132">Para obter a especificação completa, consulte [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="4107c-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
