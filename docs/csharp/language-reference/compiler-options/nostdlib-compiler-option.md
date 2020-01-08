---
title: -nostdlib (opções do compilador C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345085"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="770f9-102">-nostdlib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="770f9-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="770f9-103">**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.</span><span class="sxs-lookup"><span data-stu-id="770f9-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="770f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="770f9-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="770f9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="770f9-105">Remarks</span></span>

<span data-ttu-id="770f9-106">Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.</span><span class="sxs-lookup"><span data-stu-id="770f9-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="770f9-107">Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="770f9-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="770f9-108">Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+** .</span><span class="sxs-lookup"><span data-stu-id="770f9-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="770f9-109">Para definir essa opção do compilador no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="770f9-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="770f9-110">As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="770f9-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="770f9-111">A propriedade de compilação **não referencia mscorlib. dll** não existe nas versões mais recentes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="770f9-111">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="770f9-112">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="770f9-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="770f9-113">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="770f9-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="770f9-114">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="770f9-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="770f9-115">Modifique a propriedade **Não referenciar mscorlib.dll**.</span><span class="sxs-lookup"><span data-stu-id="770f9-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="770f9-116">Para definir essa opção do compilador via programação</span><span class="sxs-lookup"><span data-stu-id="770f9-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="770f9-117">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="770f9-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="770f9-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="770f9-118">See also</span></span>

- [<span data-ttu-id="770f9-119">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="770f9-119">C# Compiler Options</span></span>](./index.md)
