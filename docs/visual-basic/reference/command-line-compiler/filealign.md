---
title: /filealign | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5e0cd0a2a7e4c88df1087faee963f541c325b272
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="filealign"></a><span data-ttu-id="6f6c3-102">/filealign</span><span class="sxs-lookup"><span data-stu-id="6f6c3-102">/filealign</span></span>
<span data-ttu-id="6f6c3-103">Especifica onde a alinhar as seções do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6c3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f6c3-104">Syntax</span></span>  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f6c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6f6c3-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="6f6c3-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-106">Required.</span></span> <span data-ttu-id="6f6c3-107">Um valor que especifica o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="6f6c3-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="6f6c3-109">Esses valores são em bytes.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f6c3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f6c3-110">Remarks</span></span>  
 <span data-ttu-id="6f6c3-111">Você pode usar o `/filealign` opção para especificar o alinhamento das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-111">You can use the `/filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="6f6c3-112">Seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém código ou dados.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="6f6c3-113">O `/filealign` opção permite que você compilar seu aplicativo com um alinhamento padrão; a maioria dos desenvolvedores não precisam usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-113">The `/filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="6f6c3-114">Cada seção é alinhada em um limite que é um múltiplo do `/filealign` valor.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-114">Each section is aligned on a boundary that is a multiple of the `/filealign` value.</span></span> <span data-ttu-id="6f6c3-115">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-115">There is no fixed default.</span></span> <span data-ttu-id="6f6c3-116">Se `/filealign` não for especificado, o compilador escolherá um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-116">If `/filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="6f6c3-117">Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="6f6c3-118">Modificando o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f6c3-119">O `/filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6f6c3-119">The `/filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6c3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f6c3-120">See Also</span></span>  
 [<span data-ttu-id="6f6c3-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f6c3-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
