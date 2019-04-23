---
title: -baseaddress (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: aa76e3d1d30e394f28b5112e45fc72229e9a78fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295777"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="67e9e-102">-baseaddress (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="67e9e-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="67e9e-103">A opção **-baseaddress** permite especificar o endereço básico preferido em que uma DLL será carregada.</span><span class="sxs-lookup"><span data-stu-id="67e9e-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="67e9e-104">Para obter mais informações sobre quando e por que usar essa opção, consulte o [Blog do Larry Osterman](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span><span class="sxs-lookup"><span data-stu-id="67e9e-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e9e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67e9e-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="67e9e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="67e9e-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="67e9e-107">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="67e9e-107">The base address for the DLL.</span></span> <span data-ttu-id="67e9e-108">Esse endereço pode ser especificado como um número decimal, hexadecimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="67e9e-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67e9e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="67e9e-109">Remarks</span></span>  
 <span data-ttu-id="67e9e-110">O endereço básico padrão de uma DLL é definido pelo Common Language Runtime do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67e9e-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="67e9e-111">Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada.</span><span class="sxs-lookup"><span data-stu-id="67e9e-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="67e9e-112">Por exemplo, se 0x11110001 for especificado, será arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="67e9e-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="67e9e-113">Para concluir o processo de assinatura de uma DLL, use SN.EXE com a opção -R.</span><span class="sxs-lookup"><span data-stu-id="67e9e-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="67e9e-114">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67e9e-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="67e9e-115">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="67e9e-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="67e9e-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="67e9e-116">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="67e9e-117">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="67e9e-117">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="67e9e-118">Modifique a propriedade **Endereço Básico de DLL**.</span><span class="sxs-lookup"><span data-stu-id="67e9e-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="67e9e-119">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="67e9e-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e9e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67e9e-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="67e9e-121">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="67e9e-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="67e9e-122">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="67e9e-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
