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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005591"
---
# <a name="-filealign"></a><span data-ttu-id="a7e37-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="a7e37-102">-filealign</span></span>
<span data-ttu-id="a7e37-103">Especifica onde alinhar as seções do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a7e37-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7e37-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7e37-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a7e37-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="a7e37-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a7e37-106">Required.</span></span> <span data-ttu-id="a7e37-107">Um valor que especifica o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a7e37-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="a7e37-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="a7e37-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="a7e37-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="a7e37-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7e37-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7e37-110">Remarks</span></span>  
 <span data-ttu-id="a7e37-111">Você pode usar a opção `-filealign` para especificar o alinhamento das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a7e37-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="a7e37-112">As seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém o código ou os dados.</span><span class="sxs-lookup"><span data-stu-id="a7e37-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="a7e37-113">A opção `-filealign` permite compilar seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisa usar essa opção.</span><span class="sxs-lookup"><span data-stu-id="a7e37-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="a7e37-114">Cada seção é alinhada em um limite que é um múltiplo do valor `-filealign`.</span><span class="sxs-lookup"><span data-stu-id="a7e37-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="a7e37-115">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="a7e37-115">There is no fixed default.</span></span> <span data-ttu-id="a7e37-116">Se `-filealign` não for especificado, o compilador escolherá um padrão no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="a7e37-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="a7e37-117">Ao especificar o tamanho da seção, você pode alterar o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="a7e37-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="a7e37-118">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="a7e37-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7e37-119">A opção `-filealign` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="a7e37-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e37-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7e37-120">See also</span></span>

- [<span data-ttu-id="a7e37-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7e37-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
