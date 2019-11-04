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
# <a name="xamlname-grammar"></a><span data-ttu-id="a5cfb-102">Gramática XamlName</span><span class="sxs-lookup"><span data-stu-id="a5cfb-102">XamlName Grammar</span></span>
<span data-ttu-id="a5cfb-103">XamlName gramática é uma gramática específica que é definida na especificação da linguagem XAML [MS-XAML], que é reproduzida aqui para sua conveniência.</span><span class="sxs-lookup"><span data-stu-id="a5cfb-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="a5cfb-104">Da especificação XAML</span><span class="sxs-lookup"><span data-stu-id="a5cfb-104">From the XAML Specification</span></span>  
 <span data-ttu-id="a5cfb-105">A especificação [MS-XAML] define a Gramática XamlName para identificar o conjunto de identificadores simbólicos legais usado para tipos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="a5cfb-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="a5cfb-106">Os valores de cadeia de caracteres do tipo XamlName devem estar de acordo com a gramática a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5cfb-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="a5cfb-107">Que assume os seguintes valores gerais de categoria, conforme definido no banco de dados de caracteres Unicode</span><span class="sxs-lookup"><span data-stu-id="a5cfb-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="a5cfb-108">Categoria Unicode</span><span class="sxs-lookup"><span data-stu-id="a5cfb-108">Unicode category</span></span>   | <span data-ttu-id="a5cfb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5cfb-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="a5cfb-110">Lu</span><span class="sxs-lookup"><span data-stu-id="a5cfb-110">Lu</span></span>                 | <span data-ttu-id="a5cfb-111">Letra, maiúscula</span><span class="sxs-lookup"><span data-stu-id="a5cfb-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="a5cfb-112">LI</span><span class="sxs-lookup"><span data-stu-id="a5cfb-112">Ll</span></span>                 | <span data-ttu-id="a5cfb-113">Letra, minúscula</span><span class="sxs-lookup"><span data-stu-id="a5cfb-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="a5cfb-114">Lt</span><span class="sxs-lookup"><span data-stu-id="a5cfb-114">Lt</span></span>                 | <span data-ttu-id="a5cfb-115">Letra, título</span><span class="sxs-lookup"><span data-stu-id="a5cfb-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="a5cfb-116">Lm</span><span class="sxs-lookup"><span data-stu-id="a5cfb-116">Lm</span></span>                 | <span data-ttu-id="a5cfb-117">Letra, modificador</span><span class="sxs-lookup"><span data-stu-id="a5cfb-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="a5cfb-118">Lo</span><span class="sxs-lookup"><span data-stu-id="a5cfb-118">Lo</span></span>                 | <span data-ttu-id="a5cfb-119">Letra, outra</span><span class="sxs-lookup"><span data-stu-id="a5cfb-119">Letter, Other</span></span>                 |
| <span data-ttu-id="a5cfb-120">Mn</span><span class="sxs-lookup"><span data-stu-id="a5cfb-120">Mn</span></span>                 | <span data-ttu-id="a5cfb-121">Marcar, sem espaçamento</span><span class="sxs-lookup"><span data-stu-id="a5cfb-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="a5cfb-122">MC</span><span class="sxs-lookup"><span data-stu-id="a5cfb-122">Mc</span></span>                 | <span data-ttu-id="a5cfb-123">Marca, combinação de espaçamento</span><span class="sxs-lookup"><span data-stu-id="a5cfb-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="a5cfb-124">Nd</span><span class="sxs-lookup"><span data-stu-id="a5cfb-124">Nd</span></span>                 | <span data-ttu-id="a5cfb-125">Número, decimal</span><span class="sxs-lookup"><span data-stu-id="a5cfb-125">Number, Decimal</span></span>               |
| <span data-ttu-id="a5cfb-126">Nl</span><span class="sxs-lookup"><span data-stu-id="a5cfb-126">Nl</span></span>                 | <span data-ttu-id="a5cfb-127">Número, letra</span><span class="sxs-lookup"><span data-stu-id="a5cfb-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="a5cfb-128">O XAML define uma segunda gramática, DottedXamlName, usada para referências qualificadas de propriedade e evento e também para membros anexados.</span><span class="sxs-lookup"><span data-stu-id="a5cfb-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="a5cfb-129">Para obter mais informações, consulte Visão geral de <xref:System.Windows.DependencyProperty> e [XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a5cfb-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="a5cfb-130">Os valores de cadeia de caracteres do tipo DottedXamlName devem estar de acordo com a gramática a seguir:</span><span class="sxs-lookup"><span data-stu-id="a5cfb-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="a5cfb-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5cfb-131">Remarks</span></span>  
 <span data-ttu-id="a5cfb-132">Para obter a especificação completa, consulte [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="a5cfb-132">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
