---
title: -nostdlib (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 1dc0ab70ca28626c4a3f505c13ec1d6f828a4b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216129"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="a7a2c-102">-nostdlib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="a7a2c-102">-nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="a7a2c-103">**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a2c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7a2c-104">Syntax</span></span>  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="a7a2c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7a2c-105">Remarks</span></span>  
 <span data-ttu-id="a7a2c-106">Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="a7a2c-107">Se você não especificar **-nostdlib**, mscorlib.dll será importado para o programa (o mesmo que especificar **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="a7a2c-107">If you do not specify **-nostdlib**, mscorlib.dll will be imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="a7a2c-108">Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a7a2c-109">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a7a2c-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a7a2c-110">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="a7a2c-111">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="a7a2c-112">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="a7a2c-113">Modifique a propriedade **Não referenciar mscorlib.dll**.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="a7a2c-114">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7a2c-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a2c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7a2c-115">See Also</span></span>  
 [<span data-ttu-id="a7a2c-116">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="a7a2c-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
