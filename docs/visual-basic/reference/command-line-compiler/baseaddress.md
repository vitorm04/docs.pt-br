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
ms.openlocfilehash: 0550e4ad700494c8773a5d9b5b282dfa116adfed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813360"
---
# <a name="-baseaddress"></a><span data-ttu-id="fc685-102">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="fc685-102">-baseaddress</span></span>
<span data-ttu-id="fc685-103">Especifica um endereço básico padrão ao criar uma DLL.</span><span class="sxs-lookup"><span data-stu-id="fc685-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc685-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc685-104">Syntax</span></span>  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc685-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc685-105">Arguments</span></span>  
  
|<span data-ttu-id="fc685-106">Termo</span><span class="sxs-lookup"><span data-stu-id="fc685-106">Term</span></span>|<span data-ttu-id="fc685-107">Definição</span><span class="sxs-lookup"><span data-stu-id="fc685-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="fc685-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fc685-108">Required.</span></span> <span data-ttu-id="fc685-109">O endereço básico da DLL.</span><span class="sxs-lookup"><span data-stu-id="fc685-109">The base address for the DLL.</span></span> <span data-ttu-id="fc685-110">Esse endereço deve ser especificado como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="fc685-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc685-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc685-111">Remarks</span></span>  
 <span data-ttu-id="fc685-112">O endereço de base padrão para uma DLL é definido pelo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc685-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="fc685-113">Lembre-se de que a palavra de ordem inferior nesse endereço é arredondada.</span><span class="sxs-lookup"><span data-stu-id="fc685-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="fc685-114">Por exemplo, se 0x11110001 for especificado, ele é arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="fc685-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="fc685-115">Para concluir o processo de assinatura para uma DLL, use o `–R` opção da ferramenta de nomenclatura forte (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="fc685-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="fc685-116">Essa opção será ignorada se o destino não é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="fc685-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="fc685-117">Definir - baseaddress no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc685-117">To set -baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="fc685-118">1.  Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="fc685-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fc685-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="fc685-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fc685-120">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="fc685-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="fc685-121">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="fc685-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="fc685-122">4.  Modificar o valor de **endereço básico de DLL:** caixa.</span><span class="sxs-lookup"><span data-stu-id="fc685-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="fc685-123">**Observação:**      O **endereço básico de DLL:** caixa é somente leitura, a menos que o destino é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="fc685-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc685-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc685-124">See also</span></span>

- [<span data-ttu-id="fc685-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc685-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fc685-126">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc685-126">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="fc685-127">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc685-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="fc685-128">[Sn.exe (ferramenta nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="fc685-128">[Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
