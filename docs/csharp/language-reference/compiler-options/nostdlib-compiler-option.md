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
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484129"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="77e22-102">-nostdlib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="77e22-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="77e22-103">**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.</span><span class="sxs-lookup"><span data-stu-id="77e22-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="77e22-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77e22-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="77e22-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="77e22-105">Remarks</span></span>

<span data-ttu-id="77e22-106">Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.</span><span class="sxs-lookup"><span data-stu-id="77e22-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="77e22-107">Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="77e22-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="77e22-108">Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="77e22-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="77e22-109">Para definir essa opção do compilador no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77e22-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="77e22-110">As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="77e22-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="77e22-111">A propriedade de build **Não referenciar mscorlib.dll** não existe no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="77e22-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="77e22-112">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="77e22-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="77e22-113">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="77e22-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="77e22-114">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="77e22-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="77e22-115">Modifique a propriedade **Não referenciar mscorlib.dll**.</span><span class="sxs-lookup"><span data-stu-id="77e22-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="77e22-116">Para definir essa opção do compilador via programação</span><span class="sxs-lookup"><span data-stu-id="77e22-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="77e22-117">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="77e22-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="77e22-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77e22-118">See Also</span></span>

- [<span data-ttu-id="77e22-119">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="77e22-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
