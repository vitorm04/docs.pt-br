---
title: "Especificação da linguagem de rascunho de C# 6.0"
ms.date: 2017-07-01
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: reference
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, specification
- what's new [C#], language specification
- Visual C#, C# language specification
- language specification [C#]
ms.assetid: e5d5a5cc-636b-4bff-b9c8-a8edc6207c22
caps.latest.revision: 46
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
ms.sourcegitcommit: dbc7f6ad4e6ddd30b3c808840420335a0c0155ad
ms.openlocfilehash: 904b0f5bf99ed133eb505f65faaa63ca99053f5a
ms.contentlocale: pt-br
ms.lasthandoff: 08/23/2017

---
# <a name="c-60-draft-language-specification"></a><span data-ttu-id="196a6-102">Especificação da linguagem de rascunho de C# 6.0</span><span class="sxs-lookup"><span data-stu-id="196a6-102">C# 6.0 draft Language Specification</span></span>
<span data-ttu-id="196a6-103">A Especificação da Linguagem C# é a origem definitiva da sintaxe e do uso de C#.</span><span class="sxs-lookup"><span data-stu-id="196a6-103">The C# Language Specification is the definitive source for C# syntax and usage.</span></span> <span data-ttu-id="196a6-104">Essa especificação contém informações detalhadas sobre todos os aspectos da linguagem, incluindo vários pontos que a documentação do Visual C# não abrange.</span><span class="sxs-lookup"><span data-stu-id="196a6-104">This specification contains detailed information about all aspects of the language, including many points that the documentation for Visual C# doesn't cover.</span></span>

<span data-ttu-id="196a6-105">É possível baixar a versão 5.0 dessa especificação do [Centro de Download da Microsoft](http://www.microsoft.com/download/details.aspx?id=7029).</span><span class="sxs-lookup"><span data-stu-id="196a6-105">You can download version 5.0 of this specification from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=7029).</span></span> <span data-ttu-id="196a6-106">Se você instalou o Visual Studio 2015, poderá também encontrar a especificação em seu computador na pasta Arquivos de Programas (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033.</span><span class="sxs-lookup"><span data-stu-id="196a6-106">If you've installed Visual Studio 2015, you can also find the specification on your computer in the Program Files (x86)/Microsoft Visual Studio 14.0/VC#/Specifications/1033 folder.</span></span> <span data-ttu-id="196a6-107">Se você tiver outra versão do Visual Studio instalada ou se você instalou o Visual Studio em um idioma diferente do inglês, altere o caminho conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="196a6-107">If you have another version of Visual Studio installed or if you installed Visual Studio in a language other than English, change the path as appropriate.</span></span>

<span data-ttu-id="196a6-108">A versão 6.0 da especificação não foi aprovada como um padrão.</span><span class="sxs-lookup"><span data-stu-id="196a6-108">Version 6.0 of the specification has not been approved as a standard.</span></span> <span data-ttu-id="196a6-109">Este site contém a especificação [*rascunho* de C# 6.0](../../../../_csharplang/spec/lexical-structure.md).</span><span class="sxs-lookup"><span data-stu-id="196a6-109">This site contains the [*draft* C# 6.0 specification](../../../../_csharplang/spec/lexical-structure.md).</span></span> <span data-ttu-id="196a6-110">Ela é criada de arquivos markdown contidos no [repositório do GitHub dotnet/csharplang](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span><span class="sxs-lookup"><span data-stu-id="196a6-110">It is built from the markdown files contained in [the dotnet/csharplang GitHub repository](https://github.com/dotnet/csharplang/blob/master/spec/README.md).</span></span>

<span data-ttu-id="196a6-111">Problemas na especificação de rascunho devem ser criados no repositório [dotnet/csharplang](https://github.com/dotnet/csharplang/issues).</span><span class="sxs-lookup"><span data-stu-id="196a6-111">Issues on the draft specification should be created in the [dotnet/csharplang](https://github.com/dotnet/csharplang/issues) repository.</span></span> <span data-ttu-id="196a6-112">Ou, se estiver interessado em corrigir os erros que encontrar, envie uma [Solicitação de pull](https://github.com/dotnet/csharplang/pulls) para o mesmo repositório.</span><span class="sxs-lookup"><span data-stu-id="196a6-112">Or, if you are interested in fixing any errors you find, you may submit a [Pull Request](https://github.com/dotnet/csharplang/pulls) to the same repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="196a6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="196a6-113">See Also</span></span>  
 [<span data-ttu-id="196a6-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="196a6-114">C# Reference</span></span>](../../language-reference/index.md)  
 [<span data-ttu-id="196a6-115">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="196a6-115">C# Programming Guide</span></span>](../../programming-guide/index.md)

>[!div class="step-by-step"]
[<span data-ttu-id="196a6-116">Avançar</span><span class="sxs-lookup"><span data-stu-id="196a6-116">Next</span></span>](../../../../_csharplang/spec/lexical-structure.md)

