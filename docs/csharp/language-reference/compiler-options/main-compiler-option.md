---
title: -main (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602729"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="86a44-102">-main (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="86a44-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="86a44-103">Esta opção especifica a classe que contém o ponto de entrada para o programa, se mais de uma classe contiver um método **Main**.</span><span class="sxs-lookup"><span data-stu-id="86a44-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86a44-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="86a44-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="86a44-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="86a44-106">O tipo que contém o método **Main**.</span><span class="sxs-lookup"><span data-stu-id="86a44-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="86a44-107">O nome de classe informado deve ser totalmente qualificado. Ele deve incluir o namespace completo que contém a classe, seguido do nome de classe.</span><span class="sxs-lookup"><span data-stu-id="86a44-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="86a44-108">Por exemplo, quando o método `Main` é localizado dentro da classe `Program` no namespace `MyApplication.Core`, a opção do compilador deve ser `-main:MyApplication.Core.Program`.</span><span class="sxs-lookup"><span data-stu-id="86a44-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="86a44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="86a44-109">Remarks</span></span>  
 <span data-ttu-id="86a44-110">Se sua compilação incluir mais de um tipo com um método [Main](../../programming-guide/main-and-command-args/index.md), você poderá especificar qual tipo contém o método **Main** que deseja usar como o ponto de entrada para o programa.</span><span class="sxs-lookup"><span data-stu-id="86a44-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="86a44-111">Essa opção é para uso durante a compilação de um arquivo .exe.</span><span class="sxs-lookup"><span data-stu-id="86a44-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="86a44-112">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86a44-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="86a44-113">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="86a44-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="86a44-114">Clique na página de propriedades do **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="86a44-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="86a44-115">Modifique a propriedade **Objeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="86a44-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="86a44-116">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="86a44-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a44-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86a44-117">Example</span></span>  
 <span data-ttu-id="86a44-118">Compile `t2.cs` e `t3.cs`, especificando que o método **Main** será encontrado em `Test2`:</span><span class="sxs-lookup"><span data-stu-id="86a44-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="86a44-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86a44-119">See also</span></span>

- [<span data-ttu-id="86a44-120">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="86a44-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="86a44-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="86a44-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
