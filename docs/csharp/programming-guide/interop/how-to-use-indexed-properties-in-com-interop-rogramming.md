---
title: "Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 19e620415adefd6190d3896377eaf6a7cf944f28
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="d44ff-102">Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d44ff-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="d44ff-103">As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="d44ff-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="d44ff-104">As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../../csharp/language-reference/keywords/dynamic.md)) e [informações de tipo inseridas](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) para melhorar a programação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="d44ff-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="d44ff-105">Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="d44ff-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="d44ff-106">No entanto, nem todas as propriedades COM atendem a essas restrições.</span><span class="sxs-lookup"><span data-stu-id="d44ff-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="d44ff-107">Por exemplo, a propriedade [Range](http://go.microsoft.com/fwlink/?LinkId=166053) do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo.</span><span class="sxs-lookup"><span data-stu-id="d44ff-107">For example, the Excel [Range](http://go.microsoft.com/fwlink/?LinkId=166053) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="d44ff-108">No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d44ff-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 <span data-ttu-id="d44ff-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span></span>  
  
 <span data-ttu-id="d44ff-110">Em vez disso, as propriedades indexadas permitem escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d44ff-110">Indexed properties enable you to write the following instead:</span></span>  
  
 <span data-ttu-id="d44ff-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d44ff-112">O exemplo anterior também usa o recurso [argumentos opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="d44ff-112">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="d44ff-113">Da mesma forma, para definir o valor da propriedade `Value` de um objeto [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) no Visual C# 2008 e versões anteriores, dois argumentos são necessários.</span><span class="sxs-lookup"><span data-stu-id="d44ff-113">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="d44ff-114">Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo.</span><span class="sxs-lookup"><span data-stu-id="d44ff-114">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="d44ff-115">O outro fornece o valor para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="d44ff-115">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="d44ff-116">Os exemplos a seguir ilustram essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="d44ff-116">The following examples illustrate these techniques.</span></span> <span data-ttu-id="d44ff-117">Ambos definem o valor da célula A1 como `Name`.</span><span class="sxs-lookup"><span data-stu-id="d44ff-117">Both set the value of the A1 cell to `Name`.</span></span>
  
 <span data-ttu-id="d44ff-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span></span>  
  
 <span data-ttu-id="d44ff-119">Em vez disso, as propriedades indexadas permitem escrever o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d44ff-119">Indexed properties enable you to write the following code instead.</span></span>  
  
 <span data-ttu-id="d44ff-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span></span>  
  
 <span data-ttu-id="d44ff-121">Não é possível criar propriedades indexadas de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="d44ff-121">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="d44ff-122">O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.</span><span class="sxs-lookup"><span data-stu-id="d44ff-122">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d44ff-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d44ff-123">Example</span></span>  
 <span data-ttu-id="d44ff-124">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="d44ff-124">The following code shows a complete example.</span></span> <span data-ttu-id="d44ff-125">Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d44ff-125">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 <span data-ttu-id="d44ff-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d44ff-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44ff-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d44ff-127">See Also</span></span>  
 <span data-ttu-id="d44ff-128">[Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="d44ff-128">[Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span></span>  
 <span data-ttu-id="d44ff-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="d44ff-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span></span>  
 <span data-ttu-id="d44ff-130">[Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="d44ff-130">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="d44ff-131">[Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="d44ff-131">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="d44ff-132">[Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d44ff-132">[How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span></span>  
 [<span data-ttu-id="d44ff-133">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="d44ff-133">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)

