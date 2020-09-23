---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: c794d1fc1c9d20e22ffa747e3175c846341ad8ad
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097755"
---
# <a name="-baseaddress"></a><span data-ttu-id="618df-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="618df-102">-baseaddress</span></span>

<span data-ttu-id="618df-103">Especifica um endereço base padrão ao criar uma DLL.</span><span class="sxs-lookup"><span data-stu-id="618df-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="618df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="618df-104">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="618df-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="618df-105">Arguments</span></span>  
  
|<span data-ttu-id="618df-106">Termo</span><span class="sxs-lookup"><span data-stu-id="618df-106">Term</span></span>|<span data-ttu-id="618df-107">Definição</span><span class="sxs-lookup"><span data-stu-id="618df-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="618df-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="618df-108">Required.</span></span> <span data-ttu-id="618df-109">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="618df-109">The base address for the DLL.</span></span> <span data-ttu-id="618df-110">Esse endereço deve ser especificado como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="618df-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="618df-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="618df-111">Remarks</span></span>  

 <span data-ttu-id="618df-112">O endereço base padrão de uma DLL é definido pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="618df-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="618df-113">Lembre-se de que a palavra de ordem inferior nesse endereço é arredondada.</span><span class="sxs-lookup"><span data-stu-id="618df-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="618df-114">Por exemplo, se você especificar 0x11110001, ele será arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="618df-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="618df-115">Para concluir o processo de assinatura de uma DLL, use a `–R` opção da ferramenta de nomeação forte (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="618df-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="618df-116">Essa opção será ignorada se o destino não for uma DLL.</span><span class="sxs-lookup"><span data-stu-id="618df-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="618df-117">Para Set-BaseAddress no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="618df-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="618df-118">1. ter um projeto selecionado em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="618df-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="618df-119">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="618df-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="618df-120">2. Clique na guia **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="618df-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="618df-121">3. clique em **avançado**.</span><span class="sxs-lookup"><span data-stu-id="618df-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="618df-122">4. modifique o valor na caixa **endereço base do dll:** .</span><span class="sxs-lookup"><span data-stu-id="618df-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="618df-123">**Observação:**      A caixa **endereço base de dll:** é somente leitura a menos que o destino seja uma dll.</span><span class="sxs-lookup"><span data-stu-id="618df-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="618df-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="618df-124">See also</span></span>

- [<span data-ttu-id="618df-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="618df-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="618df-126">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="618df-126">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="618df-127">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="618df-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="618df-128">[Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="618df-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
