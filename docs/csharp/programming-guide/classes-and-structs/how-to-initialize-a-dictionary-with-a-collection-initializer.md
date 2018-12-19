---
title: Como inicializar um dicionário com um inicializador de coleção – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 42deee85b3a425531ddadfa96cfaff6d342d1221
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243875"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="d5fca-102">Como inicializar um dicionário com um inicializador de coleção (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d5fca-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="d5fca-103">Um <xref:System.Collections.Generic.Dictionary%602> contém uma coleção de pares de chave-valor.</span><span class="sxs-lookup"><span data-stu-id="d5fca-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="d5fca-104">Seu método <xref:System.Collections.Generic.Dictionary%602.Add*> recebe dois parâmetros, um para a chave e outro para o valor.</span><span class="sxs-lookup"><span data-stu-id="d5fca-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="d5fca-105">Para inicializar um <xref:System.Collections.Generic.Dictionary%602> ou qualquer coleção cujo método `Add` receba vários parâmetros, coloque cada conjunto de parâmetros entre chaves, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d5fca-105">To initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="d5fca-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5fca-106">Example</span></span>

<span data-ttu-id="d5fca-107">No exemplo de código a seguir, um <xref:System.Collections.Generic.Dictionary%602> é inicializado com instâncias do tipo `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="d5fca-107">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

<span data-ttu-id="d5fca-108">Observe os dois pares de chaves em cada elemento da coleção.</span><span class="sxs-lookup"><span data-stu-id="d5fca-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="d5fca-109">As chaves internas circundam o inicializador de objeto do `StudentName` e as chaves mais externas circundam o inicializador do par chave/valor que será adicionado ao `students` <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="d5fca-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="d5fca-110">Por fim, todo o inicializador de coleção do dicionário é colocado entre chaves.</span><span class="sxs-lookup"><span data-stu-id="d5fca-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="d5fca-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d5fca-111">Compiling the code</span></span>

<span data-ttu-id="d5fca-112">Para executar esse código, copie e cole a classe em um projeto de aplicativo de console do Visual C# que foi criado no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5fca-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="d5fca-113">Por padrão, esse projeto é direcionado à versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e tem uma referência a System.Core.dll e uma diretriz de uso para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="d5fca-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="d5fca-114">Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="d5fca-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5fca-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5fca-115">See also</span></span>

- [<span data-ttu-id="d5fca-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d5fca-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d5fca-117">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="d5fca-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
