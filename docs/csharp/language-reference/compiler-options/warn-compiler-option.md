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
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602399"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="83ffa-102">-warn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="83ffa-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="83ffa-103">A opção **-warn** especifica o nível de aviso a ser exibido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="83ffa-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ffa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83ffa-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="83ffa-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="83ffa-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="83ffa-106">O nível de aviso que você deseja que seja exibido para a compilação: números mais baixos mostram apenas avisos de gravidade alta; números mais altos mostram mais avisos.</span><span class="sxs-lookup"><span data-stu-id="83ffa-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="83ffa-107">Os valores válidos vão de 0 a 4:</span><span class="sxs-lookup"><span data-stu-id="83ffa-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="83ffa-108">Nível de aviso</span><span class="sxs-lookup"><span data-stu-id="83ffa-108">Warning level</span></span>|<span data-ttu-id="83ffa-109">Significado</span><span class="sxs-lookup"><span data-stu-id="83ffa-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="83ffa-110">0</span><span class="sxs-lookup"><span data-stu-id="83ffa-110">0</span></span>|<span data-ttu-id="83ffa-111">Desativa a emissão de todas as mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="83ffa-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="83ffa-112">1</span><span class="sxs-lookup"><span data-stu-id="83ffa-112">1</span></span>|<span data-ttu-id="83ffa-113">Exibe mensagens de aviso graves.</span><span class="sxs-lookup"><span data-stu-id="83ffa-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="83ffa-114">2</span><span class="sxs-lookup"><span data-stu-id="83ffa-114">2</span></span>|<span data-ttu-id="83ffa-115">Exibe os avisos do nível 1 e mais alguns avisos menos graves, como avisos sobre membros de classe ocultos.</span><span class="sxs-lookup"><span data-stu-id="83ffa-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="83ffa-116">3</span><span class="sxs-lookup"><span data-stu-id="83ffa-116">3</span></span>|<span data-ttu-id="83ffa-117">Exibe os avisos do nível 2 e mais alguns avisos menos graves, como avisos sobre expressões que sempre resultam em `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="83ffa-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="83ffa-118">4 (o padrão)</span><span class="sxs-lookup"><span data-stu-id="83ffa-118">4 (the default)</span></span>|<span data-ttu-id="83ffa-119">Exibe todos os avisos do nível 3 e também avisos informativos.</span><span class="sxs-lookup"><span data-stu-id="83ffa-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83ffa-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="83ffa-120">Remarks</span></span>  
 <span data-ttu-id="83ffa-121">Para obter informações sobre um erro ou aviso, você pode procurar o código de erro no Índice da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="83ffa-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="83ffa-122">Para outras maneiras de se obter informações sobre um erro ou aviso, consulte [Erros do compilador do C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="83ffa-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="83ffa-123">Use [-warnaserror](./warnaserror-compiler-option.md) para tratar todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="83ffa-123">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="83ffa-124">Use [-nowarn](./nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="83ffa-124">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="83ffa-125">**-w** é a forma abreviada de **-warn**.</span><span class="sxs-lookup"><span data-stu-id="83ffa-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="83ffa-126">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83ffa-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="83ffa-127">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="83ffa-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="83ffa-128">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="83ffa-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="83ffa-129">Modifique a propriedade **Nível de Aviso**.</span><span class="sxs-lookup"><span data-stu-id="83ffa-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="83ffa-130">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="83ffa-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83ffa-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83ffa-131">Example</span></span>  
 <span data-ttu-id="83ffa-132">Compilar `in.cs` e fazer com que o compilador exiba somente avisos de nível 1:</span><span class="sxs-lookup"><span data-stu-id="83ffa-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="83ffa-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="83ffa-133">See also</span></span>

- [<span data-ttu-id="83ffa-134">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="83ffa-134">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="83ffa-135">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="83ffa-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
