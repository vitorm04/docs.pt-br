---
title: "Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2538dae8f02b17a77cc1eb2798b8b38a7f1d7db2
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="4559c-102">Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4559c-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="4559c-103">As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="4559c-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="4559c-104">As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../../csharp/language-reference/keywords/dynamic.md)) e [informações de tipo inseridas](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) para melhorar a programação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="4559c-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="4559c-105">Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="4559c-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="4559c-106">No entanto, nem todas as propriedades COM atendem a essas restrições.</span><span class="sxs-lookup"><span data-stu-id="4559c-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="4559c-107">Por exemplo, a propriedade [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo.</span><span class="sxs-lookup"><span data-stu-id="4559c-107">For example, the Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="4559c-108">No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4559c-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="4559c-109">Em vez disso, as propriedades indexadas permitem escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4559c-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="4559c-110">O exemplo anterior também usa o recurso [argumentos opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="4559c-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="4559c-111">Da mesma forma, para definir o valor da propriedade `Value` de um objeto [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) no Visual C# 2008 e versões anteriores, dois argumentos são necessários.</span><span class="sxs-lookup"><span data-stu-id="4559c-111">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="4559c-112">Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo.</span><span class="sxs-lookup"><span data-stu-id="4559c-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="4559c-113">O outro fornece o valor para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="4559c-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="4559c-114">Os exemplos a seguir ilustram essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="4559c-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="4559c-115">Ambos definem o valor da célula A1 como `Name`.</span><span class="sxs-lookup"><span data-stu-id="4559c-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="4559c-116">Em vez disso, as propriedades indexadas permitem escrever o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4559c-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="4559c-117">Não é possível criar propriedades indexadas de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="4559c-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="4559c-118">O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.</span><span class="sxs-lookup"><span data-stu-id="4559c-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4559c-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4559c-119">Example</span></span>  
 <span data-ttu-id="4559c-120">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="4559c-120">The following code shows a complete example.</span></span> <span data-ttu-id="4559c-121">Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="4559c-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4559c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4559c-122">See Also</span></span>  
 [<span data-ttu-id="4559c-123">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="4559c-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="4559c-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="4559c-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="4559c-125">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="4559c-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="4559c-126">Como usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="4559c-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="4559c-127">Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#</span><span class="sxs-lookup"><span data-stu-id="4559c-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [<span data-ttu-id="4559c-128">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="4559c-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
