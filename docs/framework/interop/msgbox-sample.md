---
title: Exemplo de MsgBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b14ee9c435d36e8d6a49cbfb29a57365bcd42d6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="msgbox-sample"></a><span data-ttu-id="97a95-102">Exemplo de MsgBox</span><span class="sxs-lookup"><span data-stu-id="97a95-102">MsgBox Sample</span></span>
<span data-ttu-id="97a95-103">Esta amostra demonstra como passar tipos de cadeia de caracteres por valor como parâmetros In e quando usar os campos <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> e <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="97a95-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="97a95-104">A amostra de MsgBox usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="97a95-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="97a95-105">**MessageBox** exportada de User32.dll.</span><span class="sxs-lookup"><span data-stu-id="97a95-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="97a95-106">Nesta amostra, a classe `LibWrap` contém um protótipo gerenciado para cada função não gerenciada chamado pela classe `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="97a95-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="97a95-107">Os métodos de protótipo gerenciado `MsgBox`, `MsgBox2` e `MsgBox3` têm declarações diferentes para a mesma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="97a95-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="97a95-108">A declaração para `MsgBox2` produz uma saída incorreta na caixa de mensagem porque o tipo de caractere, especificado como ANSI, é incompatível com o ponto de entrada `MessageBoxW`, que é o nome da função Unicode.</span><span class="sxs-lookup"><span data-stu-id="97a95-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="97a95-109">A declaração `MsgBox3` cria uma incompatibilidade entre os campos **EntryPoint**, **CharSet** e **ExactSpelling**.</span><span class="sxs-lookup"><span data-stu-id="97a95-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="97a95-110">Quando chamado, `MsgBox3` gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="97a95-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="97a95-111">Para obter informações detalhadas sobre a nomeação de cadeia de caracteres e marshaling de nome, consulte [Especificando um conjunto de caracteres](../../../docs/framework/interop/specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="97a95-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="97a95-112">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="97a95-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="97a95-113">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="97a95-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="97a95-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97a95-114">See Also</span></span>  
 [<span data-ttu-id="97a95-115">Marshaling em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="97a95-115">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="97a95-116">Tipos de dados de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="97a95-116">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="97a95-117">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="97a95-117">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [<span data-ttu-id="97a95-118">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="97a95-118">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="97a95-119">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="97a95-119">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
