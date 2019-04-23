---
title: -warn (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 17dd992edbec5ce444b53ed42b2b486282618672
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315797"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="e924e-102">-warn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="e924e-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="e924e-103">A opção **-warn** especifica o nível de aviso a ser exibido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="e924e-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e924e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e924e-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="e924e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e924e-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="e924e-106">O nível de aviso que você deseja exibir para a compilação: Números mais baixos mostram apenas avisos de gravidade alta; números mais altos mostram mais avisos.</span><span class="sxs-lookup"><span data-stu-id="e924e-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="e924e-107">Os valores válidos vão de 0 a 4:</span><span class="sxs-lookup"><span data-stu-id="e924e-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="e924e-108">Nível de aviso</span><span class="sxs-lookup"><span data-stu-id="e924e-108">Warning level</span></span>|<span data-ttu-id="e924e-109">Significado</span><span class="sxs-lookup"><span data-stu-id="e924e-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="e924e-110">0</span><span class="sxs-lookup"><span data-stu-id="e924e-110">0</span></span>|<span data-ttu-id="e924e-111">Desativa a emissão de todas as mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="e924e-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="e924e-112">1</span><span class="sxs-lookup"><span data-stu-id="e924e-112">1</span></span>|<span data-ttu-id="e924e-113">Exibe mensagens de aviso graves.</span><span class="sxs-lookup"><span data-stu-id="e924e-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="e924e-114">2</span><span class="sxs-lookup"><span data-stu-id="e924e-114">2</span></span>|<span data-ttu-id="e924e-115">Exibe os avisos do nível 1 e mais alguns avisos menos graves, como avisos sobre membros de classe ocultos.</span><span class="sxs-lookup"><span data-stu-id="e924e-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="e924e-116">3</span><span class="sxs-lookup"><span data-stu-id="e924e-116">3</span></span>|<span data-ttu-id="e924e-117">Exibe os avisos do nível 2 e mais alguns avisos menos graves, como avisos sobre expressões que sempre resultam em `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="e924e-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="e924e-118">4 (o padrão)</span><span class="sxs-lookup"><span data-stu-id="e924e-118">4 (the default)</span></span>|<span data-ttu-id="e924e-119">Exibe todos os avisos do nível 3 e também avisos informativos.</span><span class="sxs-lookup"><span data-stu-id="e924e-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e924e-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="e924e-120">Remarks</span></span>  
 <span data-ttu-id="e924e-121">Para obter informações sobre um erro ou aviso, você pode procurar o código de erro no Índice da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="e924e-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="e924e-122">Para outras maneiras de se obter informações sobre um erro ou aviso, consulte [Erros do compilador do C#](../../../csharp/language-reference/compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="e924e-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="e924e-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) para tratar todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="e924e-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="e924e-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="e924e-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="e924e-125">**-w** é a forma abreviada de **-warn**.</span><span class="sxs-lookup"><span data-stu-id="e924e-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e924e-126">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e924e-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e924e-127">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="e924e-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e924e-128">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="e924e-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="e924e-129">Modifique a propriedade **Nível de Aviso**.</span><span class="sxs-lookup"><span data-stu-id="e924e-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="e924e-130">Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="e924e-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e924e-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e924e-131">Example</span></span>  
 <span data-ttu-id="e924e-132">Compilar `in.cs` e fazer com que o compilador exiba somente avisos de nível 1:</span><span class="sxs-lookup"><span data-stu-id="e924e-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e924e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e924e-133">See also</span></span>

- [<span data-ttu-id="e924e-134">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="e924e-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="e924e-135">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="e924e-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
