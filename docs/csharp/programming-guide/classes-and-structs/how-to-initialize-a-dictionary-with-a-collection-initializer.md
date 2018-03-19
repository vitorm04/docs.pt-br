---
title: "Como inicializar um dicionário com um inicializador de coleção (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="49179-102">Como inicializar um dicionário com um inicializador de coleção (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="49179-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="49179-103">Um método <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> utiliza dois parâmetros, um para a chave e um para o valor.</span><span class="sxs-lookup"><span data-stu-id="49179-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="49179-104">Para inicializar um método <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add`, use vários parâmetros, coloque cada conjunto de parâmetros entre chaves conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="49179-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49179-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49179-105">Example</span></span>  
 <span data-ttu-id="49179-106">No exemplo de código a seguir, um <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="49179-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="49179-107">Observe os dois pares de chaves em cada elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="49179-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="49179-108">As chaves internas circundam o inicializador de objeto do `StudentName` e as chaves mais externas circundam o inicializador do par de chave/valor que será adicionado ao `students`<xref:System.Collections.Generic.Dictionary`2>.</span><span class="sxs-lookup"><span data-stu-id="49179-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary`2>.</span></span> <span data-ttu-id="49179-109">Por fim, todo o inicializador de coleção do dicionário é colocado entre chaves.</span><span class="sxs-lookup"><span data-stu-id="49179-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49179-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="49179-110">Compiling the Code</span></span>  
 <span data-ttu-id="49179-111">Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49179-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="49179-112">Por padrão, esse projeto é direcionado à versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e tem uma referência a System.Core.dll e uma diretriz de uso para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="49179-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="49179-113">Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="49179-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49179-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49179-114">See Also</span></span>  
 [<span data-ttu-id="49179-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="49179-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49179-116">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="49179-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
