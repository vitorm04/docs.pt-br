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
ms.openlocfilehash: e8dfe95ef3385635f5839ecc96047911544a256e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591454"
---
# <a name="-baseaddress"></a><span data-ttu-id="9bd7d-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="9bd7d-102">-baseaddress</span></span>
<span data-ttu-id="9bd7d-103">Especifica um endereço básico padrão ao criar uma DLL.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd7d-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="9bd7d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9bd7d-105">Arguments</span></span>  
  
|<span data-ttu-id="9bd7d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="9bd7d-106">Term</span></span>|<span data-ttu-id="9bd7d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="9bd7d-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="9bd7d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-108">Required.</span></span> <span data-ttu-id="9bd7d-109">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-109">The base address for the DLL.</span></span> <span data-ttu-id="9bd7d-110">Esse endereço deve ser especificado como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd7d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd7d-111">Remarks</span></span>  
 <span data-ttu-id="9bd7d-112">O endereço de base padrão para uma DLL é definido pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-112">The default base address for a DLL is set by the .NET Framework.</span></span>  
  
 <span data-ttu-id="9bd7d-113">Lembre-se de que a palavra de ordem inferior nesse endereço é arredondada.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="9bd7d-114">Por exemplo, se 0x11110001 for especificado, ele é arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="9bd7d-115">Para concluir o processo de assinatura para uma DLL, use o `–R` opção da ferramenta de nomenclatura forte (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="9bd7d-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="9bd7d-116">Essa opção será ignorada se o destino não é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="9bd7d-117">Definir - baseaddress no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9bd7d-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="9bd7d-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9bd7d-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9bd7d-120">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9bd7d-121">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="9bd7d-122">4.  Modificar o valor de **endereço básico de DLL:** caixa.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="9bd7d-123">**Observação:**      O **endereço básico de DLL:** caixa é somente leitura, a menos que o destino é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="9bd7d-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bd7d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd7d-124">See also</span></span>

- [<span data-ttu-id="9bd7d-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bd7d-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9bd7d-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bd7d-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="9bd7d-127">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd7d-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="9bd7d-128">[Sn.exe (ferramenta nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="9bd7d-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
