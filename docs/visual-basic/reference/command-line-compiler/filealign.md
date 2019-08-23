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
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929480"
---
# <a name="-filealign"></a><span data-ttu-id="825e4-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="825e4-102">-filealign</span></span>
<span data-ttu-id="825e4-103">Especifica onde alinhar as seções do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="825e4-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="825e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="825e4-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="825e4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="825e4-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="825e4-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="825e4-106">Required.</span></span> <span data-ttu-id="825e4-107">Um valor que especifica o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="825e4-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="825e4-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="825e4-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="825e4-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="825e4-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="825e4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="825e4-110">Remarks</span></span>  
 <span data-ttu-id="825e4-111">Você pode usar a `-filealign` opção para especificar o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="825e4-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="825e4-112">As seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém o código ou os dados.</span><span class="sxs-lookup"><span data-stu-id="825e4-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="825e4-113">A `-filealign` opção permite que você compile seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisa usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="825e4-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="825e4-114">Cada seção é alinhada em um limite que é um múltiplo do `-filealign` valor.</span><span class="sxs-lookup"><span data-stu-id="825e4-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="825e4-115">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="825e4-115">There is no fixed default.</span></span> <span data-ttu-id="825e4-116">Se `-filealign` não for especificado, o compilador escolherá um padrão no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="825e4-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="825e4-117">Ao especificar o tamanho da seção, você pode alterar o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="825e4-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="825e4-118">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="825e4-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="825e4-119">A `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="825e4-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825e4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="825e4-120">See also</span></span>

- [<span data-ttu-id="825e4-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="825e4-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
