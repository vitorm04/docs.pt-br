---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 551d151ab923110c73a528a5def639fb383c889f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715914"
---
# <a name="-filealign"></a><span data-ttu-id="c5a2e-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="c5a2e-102">-filealign</span></span>
<span data-ttu-id="c5a2e-103">Especifica onde alinhar as seções do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a2e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5a2e-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="c5a2e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c5a2e-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="c5a2e-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-106">Required.</span></span> <span data-ttu-id="c5a2e-107">Um valor que especifica o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="c5a2e-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="c5a2e-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5a2e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5a2e-110">Remarks</span></span>  
 <span data-ttu-id="c5a2e-111">Você pode usar o `-filealign` opção para especificar o alinhamento das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="c5a2e-112">As seções são blocos de memória contígua em um arquivo PE (executável portátil) que contém o código ou dados.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="c5a2e-113">O `-filealign` opção permite que você compilar seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisam usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="c5a2e-114">Cada seção será alinhada em um limite que é um múltiplo do `-filealign` valor.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="c5a2e-115">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-115">There is no fixed default.</span></span> <span data-ttu-id="c5a2e-116">Se `-filealign` não for especificado, o compilador escolhe um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="c5a2e-117">Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="c5a2e-118">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5a2e-119">O `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c5a2e-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a2e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5a2e-120">See also</span></span>
- [<span data-ttu-id="c5a2e-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c5a2e-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
