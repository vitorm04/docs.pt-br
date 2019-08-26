---
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
ms.openlocfilehash: aed8b412ea1580f7dfa4f87333598d76a85b5e64
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603014"
---
# <a name="-filealign-c-compiler-options"></a><span data-ttu-id="42902-102">-filealign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="42902-102">-filealign (C# Compiler Options)</span></span>
<span data-ttu-id="42902-103">A opção **-filealign** permite que você especifique o tamanho das seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="42902-103">The **-filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42902-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42902-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="42902-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="42902-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="42902-106">Um valor que especifica o tamanho das seções no arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="42902-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="42902-107">Os valores válidos são 512, 1024, 2048, 4096 e 8192.</span><span class="sxs-lookup"><span data-stu-id="42902-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="42902-108">Esses valores estão em bytes.</span><span class="sxs-lookup"><span data-stu-id="42902-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42902-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="42902-109">Remarks</span></span>  
 <span data-ttu-id="42902-110">Cada seção será alinhada em um limite que é um múltiplo do valor **-filealign**.</span><span class="sxs-lookup"><span data-stu-id="42902-110">Each section will be aligned on a boundary that is a multiple of the **-filealign** value.</span></span> <span data-ttu-id="42902-111">Não há nenhum padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="42902-111">There is no fixed default.</span></span> <span data-ttu-id="42902-112">Se **-filealign** não é especificada, o Common Language Runtime escolhe um padrão em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="42902-112">If **-filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="42902-113">Ao especificar o tamanho da seção, você afeta o tamanho do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="42902-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="42902-114">Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.</span><span class="sxs-lookup"><span data-stu-id="42902-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="42902-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) para ver informações sobre as seções em seu arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="42902-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="42902-116">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42902-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="42902-117">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="42902-117">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="42902-118">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="42902-118">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="42902-119">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="42902-119">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="42902-120">Modifique a propriedade **Alinhamento de Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="42902-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="42902-121">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span><span class="sxs-lookup"><span data-stu-id="42902-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42902-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42902-122">See also</span></span>

- [<span data-ttu-id="42902-123">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="42902-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="42902-124">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="42902-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
