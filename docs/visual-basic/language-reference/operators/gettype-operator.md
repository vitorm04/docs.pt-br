---
title: Operador GetType (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetType
dev_langs:
- VB
helpviewer_keywords:
- GetType operator
- GetType keyword
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bde3900aa7951ca6b4b53c8e9844843e9e6bd6cc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="a6edd-102">Operador GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6edd-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="a6edd-103">Retorna um <xref:System.Type>objeto para o tipo especificado.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="a6edd-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="a6edd-104">O <xref:System.Type>objeto fornece informações sobre o tipo como suas propriedades, métodos e eventos.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="a6edd-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6edd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6edd-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6edd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6edd-106">Parameters</span></span>  
  
|<span data-ttu-id="a6edd-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a6edd-107">Parameter</span></span>|<span data-ttu-id="a6edd-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6edd-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="a6edd-109">O nome do tipo para o qual você deseja informações.</span><span class="sxs-lookup"><span data-stu-id="a6edd-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6edd-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6edd-110">Remarks</span></span>  
 <span data-ttu-id="a6edd-111">O `GetType` operador retorna o <xref:System.Type>objeto especificado `typename`.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="a6edd-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="a6edd-112">Você pode passar o nome de qualquer tipo definido em `typename`.</span><span class="sxs-lookup"><span data-stu-id="a6edd-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="a6edd-113">Isso inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6edd-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="a6edd-114">Digite quaisquer dados do Visual Basic, como `Boolean` ou `Date`.</span><span class="sxs-lookup"><span data-stu-id="a6edd-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="a6edd-115">Qualquer classe do .NET Framework, estrutura, módulo ou interface, como <xref:System.ArgumentException?displayProperty=fullName>ou <xref:System.Double?displayProperty=fullName>.</xref:System.Double?displayProperty=fullName> </xref:System.ArgumentException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6edd-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=fullName> or <xref:System.Double?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="a6edd-116">Qualquer classe, estrutura, módulo ou interface definida por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6edd-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="a6edd-117">Qualquer matriz definida por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6edd-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="a6edd-118">Qualquer delegado definido por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a6edd-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="a6edd-119">Qualquer enumeração definida pelo seu aplicativo, o .NET Framework ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6edd-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="a6edd-120">Se você deseja obter o objeto do tipo de uma variável de objeto, use o <xref:System.Type.GetType%2A?displayProperty=fullName>método.</xref:System.Type.GetType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6edd-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="a6edd-121">O `GetType` operador pode ser útil nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="a6edd-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="a6edd-122">Você deve acessar os metadados para um tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a6edd-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="a6edd-123">O <xref:System.Type>objeto fornece metadados como membros do tipo e informações de implantação.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="a6edd-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="a6edd-124">Você precisa disto, por exemplo, para refletir sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="a6edd-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="a6edd-125">Para obter mais informações, consulte <xref:System.Reflection?displayProperty=fullName>.</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6edd-125">For more information, see <xref:System.Reflection?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="a6edd-126">Você deseja comparar duas referências de objeto para ver se elas se referem a instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="a6edd-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="a6edd-127">Se Sim, `GetType` retorna referências para o mesmo <xref:System.Type>objeto.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="a6edd-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6edd-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6edd-128">Example</span></span>  
 <span data-ttu-id="a6edd-129">Os exemplos a seguir mostram o `GetType` operador em uso.</span><span class="sxs-lookup"><span data-stu-id="a6edd-129">The following examples show the `GetType` operator in use.</span></span>  
  
 <span data-ttu-id="a6edd-130">[!code-vb[VbVbalrOperators&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a6edd-130">[!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6edd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6edd-131">See Also</span></span>  
 <span data-ttu-id="a6edd-132">[Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="a6edd-132">[Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="a6edd-133"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="a6edd-133"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="a6edd-134"> [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="a6edd-134"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>
