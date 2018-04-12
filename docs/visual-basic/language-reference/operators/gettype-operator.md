---
title: Operador GetType (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="d61ba-102">Operador GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61ba-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="d61ba-103">Retorna um <xref:System.Type> objeto para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="d61ba-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="d61ba-104">O <xref:System.Type> objeto fornece informações sobre o tipo como suas propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="d61ba-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d61ba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d61ba-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d61ba-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d61ba-106">Parameters</span></span>  
  
|<span data-ttu-id="d61ba-107">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d61ba-107">Parameter</span></span>|<span data-ttu-id="d61ba-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d61ba-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="d61ba-109">O nome do tipo para o qual você deseja informações.</span><span class="sxs-lookup"><span data-stu-id="d61ba-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d61ba-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d61ba-110">Remarks</span></span>  
 <span data-ttu-id="d61ba-111">O `GetType` operador retorna o <xref:System.Type> objeto especificado `typename`.</span><span class="sxs-lookup"><span data-stu-id="d61ba-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="d61ba-112">Você pode passar o nome de qualquer tipo definido em `typename`.</span><span class="sxs-lookup"><span data-stu-id="d61ba-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="d61ba-113">Isso inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d61ba-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="d61ba-114">Tipo de dados Visual Basic, como `Boolean` ou `Date`.</span><span class="sxs-lookup"><span data-stu-id="d61ba-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="d61ba-115">Qualquer classe do .NET Framework, estrutura, módulo ou interface, como <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d61ba-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="d61ba-116">Qualquer classe, estrutura, módulo ou interface definida por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d61ba-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="d61ba-117">Qualquer matriz definida por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d61ba-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="d61ba-118">Qualquer delegado definido pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d61ba-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="d61ba-119">Qualquer enumeração definida por seu aplicativo, o .NET Framework ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d61ba-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="d61ba-120">Se você deseja obter o objeto do tipo de uma variável de objeto, use o <xref:System.Type.GetType%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="d61ba-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d61ba-121">O `GetType` operador pode ser útil nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="d61ba-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="d61ba-122">Você deve acessar os metadados para um tipo em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d61ba-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="d61ba-123">O <xref:System.Type> objeto fornece metadados como membros do tipo e informações de implantação.</span><span class="sxs-lookup"><span data-stu-id="d61ba-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="d61ba-124">Você precisa disto, por exemplo, para refletir sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="d61ba-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="d61ba-125">Para obter mais informações, consulte <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d61ba-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="d61ba-126">Você deseja comparar duas referências de objeto para ver se elas se referem a instâncias do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="d61ba-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="d61ba-127">Se isso ocorrer, `GetType` retorna referências para o mesmo <xref:System.Type> objeto.</span><span class="sxs-lookup"><span data-stu-id="d61ba-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d61ba-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d61ba-128">Example</span></span>  
 <span data-ttu-id="d61ba-129">Os exemplos a seguir mostram o `GetType` operador em uso.</span><span class="sxs-lookup"><span data-stu-id="d61ba-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d61ba-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d61ba-130">See Also</span></span>  
 [<span data-ttu-id="d61ba-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d61ba-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d61ba-132">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="d61ba-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d61ba-133">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="d61ba-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
