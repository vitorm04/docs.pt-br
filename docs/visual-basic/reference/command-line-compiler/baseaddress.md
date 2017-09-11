---
title: /baseaddress | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
dev_langs:
- VB
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5687f119a57e0e54eca4df8f91fdf5e8b2775f82
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="baseaddress"></a><span data-ttu-id="02c7d-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="02c7d-102">/baseaddress</span></span>
<span data-ttu-id="02c7d-103">Especifica um endereço básico padrão ao criar uma DLL.</span><span class="sxs-lookup"><span data-stu-id="02c7d-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02c7d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02c7d-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="02c7d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="02c7d-105">Arguments</span></span>  
  
|<span data-ttu-id="02c7d-106">Termo</span><span class="sxs-lookup"><span data-stu-id="02c7d-106">Term</span></span>|<span data-ttu-id="02c7d-107">Definição</span><span class="sxs-lookup"><span data-stu-id="02c7d-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="02c7d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="02c7d-108">Required.</span></span> <span data-ttu-id="02c7d-109">O endereço base para a DLL.</span><span class="sxs-lookup"><span data-stu-id="02c7d-109">The base address for the DLL.</span></span> <span data-ttu-id="02c7d-110">Esse endereço deve ser especificado como um número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="02c7d-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02c7d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="02c7d-111">Remarks</span></span>  
 <span data-ttu-id="02c7d-112">O endereço de base padrão para uma DLL é definido pelo [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="02c7d-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
 <span data-ttu-id="02c7d-113">Lembre-se de que a palavra de ordem inferior esse endereço é arredondada.</span><span class="sxs-lookup"><span data-stu-id="02c7d-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="02c7d-114">Por exemplo, se você especificar 0x11110001, ele é arredondado para 0x11110000.</span><span class="sxs-lookup"><span data-stu-id="02c7d-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="02c7d-115">Para concluir o processo de assinatura para uma DLL, use o `–R` opção da ferramenta de nomeação forte (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="02c7d-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="02c7d-116">Essa opção será ignorada se o destino não é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="02c7d-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="02c7d-117">Definir /baseaddress no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="02c7d-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="02c7d-118">1.  Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="02c7d-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="02c7d-119">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="02c7d-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="02c7d-120">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="02c7d-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="02c7d-121">2.  Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="02c7d-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="02c7d-122">3.  Clique em **Avançadas**.</span><span class="sxs-lookup"><span data-stu-id="02c7d-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="02c7d-123">4.  Modificar o valor de **endereço base de DLL:** caixa.</span><span class="sxs-lookup"><span data-stu-id="02c7d-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="02c7d-124">**Observação:** o **endereço base de DLL:** caixa é somente leitura, a menos que o destino é uma DLL.</span><span class="sxs-lookup"><span data-stu-id="02c7d-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02c7d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c7d-125">See Also</span></span>  
 <span data-ttu-id="02c7d-126">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="02c7d-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="02c7d-127"> [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="02c7d-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="02c7d-128"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="02c7d-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="02c7d-129"> [Sn.exe (ferramenta de nome forte)](https://msdn.microsoft.com/library/k5b5tt23)</span><span class="sxs-lookup"><span data-stu-id="02c7d-129"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)</span></span>
