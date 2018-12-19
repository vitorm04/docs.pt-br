---
title: '&lt;summary&gt; – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 5aaa9b08b422c06cc6b009e5e9d781e8be46af7e
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237292"
---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="94d57-102">&lt;summary&gt; (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="94d57-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="94d57-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94d57-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94d57-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94d57-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="94d57-105">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="94d57-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d57-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="94d57-106">Remarks</span></span>  
 <span data-ttu-id="94d57-107">A marca \<summary> deve ser usada para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="94d57-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="94d57-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) para adicionar mais informações a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="94d57-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="94d57-109">Use o [atributo cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) para habilitar ferramentas de documentação como [Sandcastle](https://github.com/EWSoftware/SHFB) a criarem hiperlinks internos para páginas de documentação para elementos de código.</span><span class="sxs-lookup"><span data-stu-id="94d57-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="94d57-110">O texto da marca \<summary> é a única fonte de informações sobre o tipo no IntelliSense e também é exibido na janela Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="94d57-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="94d57-111">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="94d57-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="94d57-112">Para criar a documentação final baseada no arquivo gerado pelo compilador, você pode criar uma ferramenta personalizada ou usar uma ferramenta como o [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="94d57-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d57-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94d57-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]  
  
 <span data-ttu-id="94d57-114">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="94d57-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="94d57-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94d57-115">Example</span></span>  
 <span data-ttu-id="94d57-116">O exemplo a seguir mostra como fazer uma referência `cref` para um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="94d57-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]  
  
 <span data-ttu-id="94d57-117">O exemplo anterior produz o seguinte arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="94d57-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94d57-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94d57-118">See Also</span></span>

- [<span data-ttu-id="94d57-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="94d57-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="94d57-120">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="94d57-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
