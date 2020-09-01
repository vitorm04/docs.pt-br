---
description: -filealign (opções do compilador C#)
title: -filealign (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: d4abe6c3825de211d737f402a745c8953adca4b8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125703"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="6d42f-103">-filealign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="6d42f-103">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="6d42f-104">A opção **-filealign** permite que você especifique o tamanho das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6d42f-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d42f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d42f-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d42f-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6d42f-106">Arguments</span></span>  
 `number`  
 <span data-ttu-id="6d42f-107">Um valor que especifica o tamanho das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6d42f-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="6d42f-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="6d42f-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="6d42f-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="6d42f-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d42f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d42f-110">Remarks</span></span>  
 <span data-ttu-id="6d42f-111">Cada seção será alinhada em um limite que é um múltiplo do valor **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="6d42f-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="6d42f-112">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="6d42f-112">There is no fixed default.</span></span> <span data-ttu-id="6d42f-113">Se **-filealign** não é especificada, o Common Language Runtime escolhe um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="6d42f-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="6d42f-114">Ao especificar o tamanho da seção, você afeta o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6d42f-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="6d42f-115">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="6d42f-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="6d42f-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) para ver informações sobre as seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6d42f-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6d42f-117">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d42f-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6d42f-118">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="6d42f-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6d42f-119">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="6d42f-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6d42f-120">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="6d42f-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="6d42f-121">Modifique a propriedade **Alinhamento de Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="6d42f-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="6d42f-122">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d42f-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d42f-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="6d42f-123">See also</span></span>

- [<span data-ttu-id="6d42f-124">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="6d42f-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6d42f-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="6d42f-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
