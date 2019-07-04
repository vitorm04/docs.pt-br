---
title: 'Como: usar propriedades indexadas na programação para interoperabilidade COM – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: d2b992131bb5722b8a10ec4a71fc42602c98a12c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347615"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="a9e72-102">Como: usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="a9e72-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="a9e72-103">As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="a9e72-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="a9e72-104">As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../../csharp/language-reference/keywords/dynamic.md)) e [informações de tipo inseridas](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) para melhorar a programação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="a9e72-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="a9e72-105">Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="a9e72-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="a9e72-106">No entanto, nem todas as propriedades COM atendem a essas restrições.</span><span class="sxs-lookup"><span data-stu-id="a9e72-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="a9e72-107">Por exemplo, a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo.</span><span class="sxs-lookup"><span data-stu-id="a9e72-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="a9e72-108">No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9e72-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="a9e72-109">Em vez disso, as propriedades indexadas permitem escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a9e72-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
>  <span data-ttu-id="a9e72-110">O exemplo anterior também usa o recurso [argumentos opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="a9e72-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="a9e72-111">Da mesma forma, para definir o valor da propriedade `Value` de um objeto <xref:Microsoft.Office.Interop.Excel.Range> no C# 3.0 e versões anteriores, são necessários dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="a9e72-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="a9e72-112">Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo.</span><span class="sxs-lookup"><span data-stu-id="a9e72-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="a9e72-113">O outro fornece o valor para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="a9e72-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="a9e72-114">Os exemplos a seguir ilustram essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="a9e72-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="a9e72-115">Ambos definem o valor da célula A1 como `Name`.</span><span class="sxs-lookup"><span data-stu-id="a9e72-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="a9e72-116">Em vez disso, as propriedades indexadas permitem escrever o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a9e72-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="a9e72-117">Não é possível criar propriedades indexadas de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="a9e72-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="a9e72-118">O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.</span><span class="sxs-lookup"><span data-stu-id="a9e72-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e72-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a9e72-119">Example</span></span>  
 <span data-ttu-id="a9e72-120">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="a9e72-120">The following code shows a complete example.</span></span> <span data-ttu-id="a9e72-121">Para saber mais sobre como configurar um projeto que acessa a API do Office, confira [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="a9e72-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e72-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9e72-122">See also</span></span>

- [<span data-ttu-id="a9e72-123">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="a9e72-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="a9e72-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="a9e72-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="a9e72-125">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="a9e72-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="a9e72-126">Como: usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="a9e72-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="a9e72-127">Como: acessar objetos de interoperabilidade do Office usando recursos do Visual C#</span><span class="sxs-lookup"><span data-stu-id="a9e72-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="a9e72-128">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="a9e72-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
