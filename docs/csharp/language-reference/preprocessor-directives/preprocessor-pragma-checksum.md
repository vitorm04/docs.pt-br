---
title: '#pragma checksum – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 4103b6262fc5085c1204f423a36c9c5c2053b497
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605657"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="a8068-102">#pragma checksum (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a8068-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="a8068-103">Gera somas de verificação para os arquivos de origem para ajudar na depuração de páginas do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8068-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8068-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8068-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8068-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8068-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="a8068-106">O nome do arquivo que exige o monitoramento de alterações ou atualizações.</span><span class="sxs-lookup"><span data-stu-id="a8068-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="a8068-107">O GUID (identificador global exclusivo) do algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="a8068-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="a8068-108">A cadeia de caracteres de dígitos hexadecimais que representa os bytes da soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="a8068-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="a8068-109">Deve ser um número par de dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="a8068-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="a8068-110">Um número ímpar de dígitos resulta em um aviso em tempo de compilação e a diretiva é ignorada.</span><span class="sxs-lookup"><span data-stu-id="a8068-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8068-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8068-111">Remarks</span></span>  
 <span data-ttu-id="a8068-112">O depurador do Visual Studio usa uma soma de verificação para certificar-se de sempre encontrar a fonte correta.</span><span class="sxs-lookup"><span data-stu-id="a8068-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="a8068-113">O compilador calcula a soma de verificação para um arquivo de origem e, em seguida, emite a saída no arquivo PDB (banco de dados do programa).</span><span class="sxs-lookup"><span data-stu-id="a8068-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="a8068-114">Em seguida, o depurador usa o PDB para comparar com a soma de verificação que ele calcula para o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="a8068-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="a8068-115">Essa solução não funciona para projetos do ASP.NET, porque é a soma de verificação calculada é para o arquivo de origem gerado e não para o arquivo .aspx.</span><span class="sxs-lookup"><span data-stu-id="a8068-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="a8068-116">Para resolver esse problema, a `#pragma checksum` fornece suporte à soma de verificação para páginas do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a8068-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="a8068-117">Quando você cria um projeto do ASP.NET em Visual C#, o arquivo de origem gerado contém uma soma de verificação para o arquivo .aspx, do qual a fonte é gerada.</span><span class="sxs-lookup"><span data-stu-id="a8068-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="a8068-118">Então, o compilador grava essas informações no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="a8068-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="a8068-119">Se o compilador não encontrar uma diretiva `#pragma checksum` no arquivo, ele calcula a soma de verificação e grava o valor no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="a8068-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8068-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8068-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8068-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8068-121">See also</span></span>

- [<span data-ttu-id="a8068-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a8068-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a8068-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a8068-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a8068-124">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="a8068-124">C# Preprocessor Directives</span></span>](./index.md)
