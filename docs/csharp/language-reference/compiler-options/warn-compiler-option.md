---
description: -warn (opções do compilador C#)
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
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d59274423e6f9844d3ab22f3ac513ba1a05d7f07
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171345"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="97ffd-103">-warn (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="97ffd-103">-warn (C# Compiler Options)</span></span>

<span data-ttu-id="97ffd-104">A opção **-warn** especifica o nível de aviso a ser exibido pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="97ffd-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97ffd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97ffd-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="97ffd-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="97ffd-106">Arguments</span></span>  

 `option`  
 <span data-ttu-id="97ffd-107">O nível de aviso que você deseja que seja exibido para a compilação: números mais baixos mostram apenas avisos de gravidade alta; números mais altos mostram mais avisos.</span><span class="sxs-lookup"><span data-stu-id="97ffd-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="97ffd-108">O valor deve ser zero ou um inteiro positivo:</span><span class="sxs-lookup"><span data-stu-id="97ffd-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="97ffd-109">Nível de aviso</span><span class="sxs-lookup"><span data-stu-id="97ffd-109">Warning level</span></span>|<span data-ttu-id="97ffd-110">Significado</span><span class="sxs-lookup"><span data-stu-id="97ffd-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="97ffd-111">0</span><span class="sxs-lookup"><span data-stu-id="97ffd-111">0</span></span>|<span data-ttu-id="97ffd-112">Desativa a emissão de todas as mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="97ffd-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="97ffd-113">1</span><span class="sxs-lookup"><span data-stu-id="97ffd-113">1</span></span>|<span data-ttu-id="97ffd-114">Exibe mensagens de aviso graves.</span><span class="sxs-lookup"><span data-stu-id="97ffd-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="97ffd-115">2</span><span class="sxs-lookup"><span data-stu-id="97ffd-115">2</span></span>|<span data-ttu-id="97ffd-116">Exibe os avisos do nível 1 e mais alguns avisos menos graves, como avisos sobre membros de classe ocultos.</span><span class="sxs-lookup"><span data-stu-id="97ffd-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="97ffd-117">3</span><span class="sxs-lookup"><span data-stu-id="97ffd-117">3</span></span>|<span data-ttu-id="97ffd-118">Exibe os avisos do nível 2 e mais alguns avisos menos graves, como avisos sobre expressões que sempre resultam em `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="97ffd-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="97ffd-119">4 (o padrão)</span><span class="sxs-lookup"><span data-stu-id="97ffd-119">4 (the default)</span></span>|<span data-ttu-id="97ffd-120">Exibe todos os avisos do nível 3 e também avisos informativos.</span><span class="sxs-lookup"><span data-stu-id="97ffd-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="97ffd-121">5</span><span class="sxs-lookup"><span data-stu-id="97ffd-121">5</span></span>|<span data-ttu-id="97ffd-122">Exibe avisos de nível 4 mais [avisos adicionais](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) do compilador fornecidos com o C# 9,0.</span><span class="sxs-lookup"><span data-stu-id="97ffd-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="97ffd-123">Maior que 5</span><span class="sxs-lookup"><span data-stu-id="97ffd-123">Greater than 5</span></span>|<span data-ttu-id="97ffd-124">Qualquer valor maior que 5 será tratado como 5.</span><span class="sxs-lookup"><span data-stu-id="97ffd-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="97ffd-125">Em geral, você coloca um valor grande arbitrário (por exemplo, `9999` ) para certificar-se de sempre ter todos os avisos se o compilador for atualizado com novos níveis de aviso.</span><span class="sxs-lookup"><span data-stu-id="97ffd-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="97ffd-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="97ffd-126">Remarks</span></span>  

 <span data-ttu-id="97ffd-127">Para obter informações sobre um erro ou aviso, você pode procurar o código de erro no Índice da Ajuda.</span><span class="sxs-lookup"><span data-stu-id="97ffd-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="97ffd-128">Para outras maneiras de se obter informações sobre um erro ou aviso, consulte [Erros do compilador do C#](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="97ffd-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="97ffd-129">Use [-warnaserror](./warnaserror-compiler-option.md) para tratar todos os avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="97ffd-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="97ffd-130">Use [-nowarn](./nowarn-compiler-option.md) para desabilitar determinados avisos.</span><span class="sxs-lookup"><span data-stu-id="97ffd-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="97ffd-131">**-w** é a forma abreviada de **-warn**.</span><span class="sxs-lookup"><span data-stu-id="97ffd-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="97ffd-132">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="97ffd-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="97ffd-133">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="97ffd-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="97ffd-134">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="97ffd-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="97ffd-135">Modifique a propriedade **Nível de Aviso**.</span><span class="sxs-lookup"><span data-stu-id="97ffd-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="97ffd-136">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="97ffd-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ffd-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97ffd-137">Example</span></span>  

 <span data-ttu-id="97ffd-138">Compilar `in.cs` e fazer com que o compilador exiba somente avisos de nível 1:</span><span class="sxs-lookup"><span data-stu-id="97ffd-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="97ffd-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="97ffd-139">See also</span></span>

- [<span data-ttu-id="97ffd-140">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="97ffd-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="97ffd-141">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="97ffd-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
