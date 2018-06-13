---
title: -/filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9c854060e5254cedc6c1004ac3e4f25fbdbbd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650661"
---
# <a name="-filealign"></a><span data-ttu-id="582f9-102">-/filealign</span><span class="sxs-lookup"><span data-stu-id="582f9-102">-filealign</span></span>
<span data-ttu-id="582f9-103">Especifica onde a alinhar as seções do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="582f9-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="582f9-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="582f9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="582f9-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="582f9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="582f9-106">Required.</span></span> <span data-ttu-id="582f9-107">Um valor que especifica o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="582f9-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="582f9-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="582f9-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="582f9-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="582f9-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="582f9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="582f9-110">Remarks</span></span>  
 <span data-ttu-id="582f9-111">Você pode usar o `-filealign` opção para especificar o alinhamento das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="582f9-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="582f9-112">Seções são blocos de memória contígua em um arquivo PE (executável portátil) que contém códigos ou dados.</span><span class="sxs-lookup"><span data-stu-id="582f9-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="582f9-113">O `-filealign` opção permite que você compilar o aplicativo com um alinhamento padrão; a maioria dos desenvolvedores não precisa usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="582f9-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="582f9-114">Cada seção está alinhada em um limite que é um múltiplo do `-filealign` valor.</span><span class="sxs-lookup"><span data-stu-id="582f9-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="582f9-115">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="582f9-115">There is no fixed default.</span></span> <span data-ttu-id="582f9-116">Se `-filealign` não for especificado, o compilador escolhe um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="582f9-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="582f9-117">Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="582f9-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="582f9-118">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="582f9-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="582f9-119">O `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="582f9-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582f9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="582f9-120">See Also</span></span>  
 [<span data-ttu-id="582f9-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="582f9-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
