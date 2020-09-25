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
ms.openlocfilehash: 4b61217a3d6812ea3ab036f82d49bba05c20629e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173237"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="83b5b-103">-filealign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="83b5b-103">-filealign (C# Compiler Options)</span></span>

<span data-ttu-id="83b5b-104">A opção **-filealign** permite que você especifique o tamanho das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="83b5b-104">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b5b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83b5b-105">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="83b5b-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="83b5b-106">Arguments</span></span>  

 `number`  
 <span data-ttu-id="83b5b-107">Um valor que especifica o tamanho das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="83b5b-107">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="83b5b-108">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="83b5b-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="83b5b-109">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="83b5b-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83b5b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="83b5b-110">Remarks</span></span>  

 <span data-ttu-id="83b5b-111">Cada seção será alinhada em um limite que é um múltiplo do valor **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="83b5b-111">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="83b5b-112">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="83b5b-112">There is no fixed default.</span></span> <span data-ttu-id="83b5b-113">Se **-filealign** não é especificada, o Common Language Runtime escolhe um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="83b5b-113">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="83b5b-114">Ao especificar o tamanho da seção, você afeta o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="83b5b-114">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="83b5b-115">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="83b5b-115">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="83b5b-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) para ver informações sobre as seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="83b5b-116">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="83b5b-117">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83b5b-117">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="83b5b-118">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="83b5b-118">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="83b5b-119">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="83b5b-119">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="83b5b-120">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="83b5b-120">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="83b5b-121">Modifique a propriedade **Alinhamento de Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="83b5b-121">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="83b5b-122">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="83b5b-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b5b-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="83b5b-123">See also</span></span>

- [<span data-ttu-id="83b5b-124">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="83b5b-124">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="83b5b-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="83b5b-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
