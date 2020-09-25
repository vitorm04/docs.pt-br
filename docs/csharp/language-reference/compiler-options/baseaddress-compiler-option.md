---
description: -baseaddress (opções do compilador C#)
title: -baseaddress (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 76da496f7045f12778bba273947b913be1b94e3e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196839"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="ad264-103">-baseaddress (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="ad264-103">-baseaddress (C# Compiler Options)</span></span>

<span data-ttu-id="ad264-104">A opção **-baseaddress** permite especificar o endereço básico preferido em que uma DLL será carregada.</span><span class="sxs-lookup"><span data-stu-id="ad264-104">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="ad264-105">Para obter mais informações sobre quando e por que usar essa opção, consulte o [Blog do Larry Osterman](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span><span class="sxs-lookup"><span data-stu-id="ad264-105">For more information about when and why to use this option, see [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad264-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad264-106">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad264-107">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ad264-107">Arguments</span></span>  

 `address`  
 <span data-ttu-id="ad264-108">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="ad264-108">The base address for the DLL.</span></span> <span data-ttu-id="ad264-109">Esse endereço pode ser especificado como um número decimal, hexadecimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="ad264-109">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad264-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ad264-110">Remarks</span></span>  

 <span data-ttu-id="ad264-111">O endereço base padrão de uma DLL é definido pelo Common Language Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="ad264-111">The default base address for a DLL is set by the .NET common language runtime.</span></span>  
  
 <span data-ttu-id="ad264-112">Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada.</span><span class="sxs-lookup"><span data-stu-id="ad264-112">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="ad264-113">Por exemplo, se 0x11110001 for especificado, será arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="ad264-113">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="ad264-114">Para concluir o processo de assinatura de uma DLL, use SN.EXE com a opção -R.</span><span class="sxs-lookup"><span data-stu-id="ad264-114">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ad264-115">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ad264-115">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ad264-116">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="ad264-116">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ad264-117">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ad264-117">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ad264-118">Clique no botão **Avançado** .</span><span class="sxs-lookup"><span data-stu-id="ad264-118">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="ad264-119">Modifique a propriedade **Endereço Básico de DLL**.</span><span class="sxs-lookup"><span data-stu-id="ad264-119">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="ad264-120">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad264-120">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad264-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="ad264-121">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ad264-122">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="ad264-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ad264-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="ad264-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
