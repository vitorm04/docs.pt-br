---
title: "-baseaddress (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dllbase
dev_langs:
- CSharp
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91193ae794957b5045a225614d6322e86d18d459
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="3cb87-102">/baseaddress (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="3cb87-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="3cb87-103">A opção **/baseaddress** permite especificar o endereço básico preferido em que uma DLL será carregada.</span><span class="sxs-lookup"><span data-stu-id="3cb87-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="3cb87-104">Para obter mais informações sobre quando e por que usar essa opção, consulte [Melhorando o Tempo de Inicialização do Aplicativo](http://go.microsoft.com/fwlink/?LinkId=107043) e [Log da Web do Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).</span><span class="sxs-lookup"><span data-stu-id="3cb87-104">For more information about when and why to use this option, see [Improving Application Startup Time](http://go.microsoft.com/fwlink/?LinkId=107043) and [Larry Osterman's WebLog](http://go.microsoft.com/fwlink/?LinkId=107044).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb87-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3cb87-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cb87-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="3cb87-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="3cb87-107">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="3cb87-107">The base address for the DLL.</span></span> <span data-ttu-id="3cb87-108">Esse endereço pode ser especificado como um número decimal, hexadecimal ou octal.</span><span class="sxs-lookup"><span data-stu-id="3cb87-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cb87-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3cb87-109">Remarks</span></span>  
 <span data-ttu-id="3cb87-110">O endereço básico padrão de uma DLL é definido pelo Common Language Runtime do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3cb87-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="3cb87-111">Lembre-se de que a palavra de ordem inferior nesse endereço será arredondada.</span><span class="sxs-lookup"><span data-stu-id="3cb87-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="3cb87-112">Por exemplo, se 0x11110001 for especificado, será arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="3cb87-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="3cb87-113">Para concluir o processo de assinatura de uma DLL, use SN.EXE com a opção -R.</span><span class="sxs-lookup"><span data-stu-id="3cb87-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3cb87-114">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3cb87-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3cb87-115">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="3cb87-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="3cb87-116">Clique na página de propriedades **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="3cb87-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="3cb87-117">Clique no botão **Avançado**.</span><span class="sxs-lookup"><span data-stu-id="3cb87-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="3cb87-118">Modifique a propriedade **Endereço Básico de DLL**.</span><span class="sxs-lookup"><span data-stu-id="3cb87-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="3cb87-119">Para definir programaticamente essa opção do compilador, confira <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cb87-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb87-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cb87-120">See Also</span></span>  
 <span data-ttu-id="3cb87-121"><xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3cb87-121"><xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="3cb87-122">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="3cb87-122">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="3cb87-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="3cb87-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

