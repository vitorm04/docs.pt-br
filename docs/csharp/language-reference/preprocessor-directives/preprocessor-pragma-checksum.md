---
title: "#<a name=\"pragma-checksum-c-reference\"></a>soma de verificação pragma (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma checksum'
helpviewer_keywords: '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="669da-102">#pragma checksum (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="669da-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="669da-103">Gera somas de verificação para os arquivos de origem para ajudar na depuração de páginas do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="669da-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="669da-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="669da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669da-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="669da-106">O nome do arquivo que exige o monitoramento de alterações ou atualizações.</span><span class="sxs-lookup"><span data-stu-id="669da-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="669da-107">O GUID (identificador global exclusivo) do arquivo.</span><span class="sxs-lookup"><span data-stu-id="669da-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="669da-108">A cadeia de caracteres de dígitos hexadecimais que representa os bytes da soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="669da-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="669da-109">Deve ser um número par de dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="669da-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="669da-110">Um número ímpar de dígitos resulta em um aviso em tempo de compilação e a diretiva é ignorada.</span><span class="sxs-lookup"><span data-stu-id="669da-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="669da-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="669da-111">Remarks</span></span>  
 <span data-ttu-id="669da-112">O depurador do Visual Studio usa uma soma de verificação para certificar-se de sempre encontrar a fonte correta.</span><span class="sxs-lookup"><span data-stu-id="669da-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="669da-113">O compilador calcula a soma de verificação para um arquivo de origem e, em seguida, emite a saída no arquivo PDB (banco de dados do programa).</span><span class="sxs-lookup"><span data-stu-id="669da-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="669da-114">Em seguida, o depurador usa o PDB para comparar com a soma de verificação que ele calcula para o arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="669da-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="669da-115">Essa solução não funciona para projetos [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], porque é a soma de verificação calculada é para o arquivo de origem gerado e não para o arquivo .aspx.</span><span class="sxs-lookup"><span data-stu-id="669da-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="669da-116">Para resolver esse problema, a `#pragma checksum` fornece suporte à soma de verificação para páginas do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="669da-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="669da-117">Quando você cria um projeto do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] no [!INCLUDE[csprcs](~/includes/csprcs-md.md)], o arquivo de origem gerado contém uma soma de verificação para o arquivo .aspx, do qual a fonte é gerada.</span><span class="sxs-lookup"><span data-stu-id="669da-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="669da-118">Então, o compilador grava essas informações no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="669da-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="669da-119">Se o compilador não encontrar uma diretiva `#pragma checksum` no arquivo, ele calcula a soma de verificação e grava o valor no arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="669da-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="669da-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669da-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="669da-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669da-121">See Also</span></span>  
 [<span data-ttu-id="669da-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="669da-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="669da-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="669da-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="669da-124">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="669da-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
