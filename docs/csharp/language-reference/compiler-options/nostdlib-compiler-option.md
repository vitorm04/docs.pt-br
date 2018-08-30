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
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935518"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="99e04-102">-nostdlib (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="99e04-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="99e04-103">**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.</span><span class="sxs-lookup"><span data-stu-id="99e04-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="99e04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99e04-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="99e04-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="99e04-105">Remarks</span></span>

<span data-ttu-id="99e04-106">Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.</span><span class="sxs-lookup"><span data-stu-id="99e04-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="99e04-107">Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="99e04-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="99e04-108">Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="99e04-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="99e04-109">Para definir essa opção do compilador no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99e04-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="99e04-110">As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores).</span><span class="sxs-lookup"><span data-stu-id="99e04-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="99e04-111">A propriedade de build **Não referenciar mscorlib.dll** não existe no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="99e04-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="99e04-112">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="99e04-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="99e04-113">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="99e04-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="99e04-114">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="99e04-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="99e04-115">Modifique a propriedade **Não referenciar mscorlib.dll**.</span><span class="sxs-lookup"><span data-stu-id="99e04-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="99e04-116">Para definir essa opção do compilador via programação</span><span class="sxs-lookup"><span data-stu-id="99e04-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="99e04-117">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="99e04-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="99e04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99e04-118">See Also</span></span>

- [<span data-ttu-id="99e04-119">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="99e04-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
