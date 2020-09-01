---
description: -nostdlib (opções do compilador C#)
title: -nostdlib (opções do compilador C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125092"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="262dd-103">-nostdlib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="262dd-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="262dd-104">**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.</span><span class="sxs-lookup"><span data-stu-id="262dd-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="262dd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="262dd-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="262dd-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="262dd-106">Remarks</span></span>

<span data-ttu-id="262dd-107">Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.</span><span class="sxs-lookup"><span data-stu-id="262dd-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="262dd-108">Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="262dd-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="262dd-109">Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="262dd-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="262dd-110">Para definir essa opção do compilador no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="262dd-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="262dd-111">As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="262dd-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="262dd-112">A propriedade não **referenciar mscorlib.dll** Build não existe em versões mais recentes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="262dd-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="262dd-113">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="262dd-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="262dd-114">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="262dd-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="262dd-115">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="262dd-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="262dd-116">Modifique a propriedade **Não referenciar mscorlib.dll**.</span><span class="sxs-lookup"><span data-stu-id="262dd-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="262dd-117">Para definir essa opção do compilador via programação</span><span class="sxs-lookup"><span data-stu-id="262dd-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="262dd-118">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="262dd-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="262dd-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="262dd-119">See also</span></span>

- [<span data-ttu-id="262dd-120">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="262dd-120">C# Compiler Options</span></span>](./index.md)
