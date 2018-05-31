---
title: Exemplo de MsgBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c4d38b60f349f0ecb87204cb980dd6681a8cc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388694"
---
# <a name="msgbox-sample"></a><span data-ttu-id="5bd2d-102">Exemplo de MsgBox</span><span class="sxs-lookup"><span data-stu-id="5bd2d-102">MsgBox Sample</span></span>
<span data-ttu-id="5bd2d-103">Esta amostra demonstra como passar tipos de cadeia de caracteres por valor como parâmetros In e quando usar os campos <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> e <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="5bd2d-104">A amostra de MsgBox usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="5bd2d-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="5bd2d-105">**MessageBox** exportada de User32.dll.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="5bd2d-106">Nesta amostra, a classe `LibWrap` contém um protótipo gerenciado para cada função não gerenciada chamado pela classe `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="5bd2d-107">Os métodos de protótipo gerenciado `MsgBox`, `MsgBox2` e `MsgBox3` têm declarações diferentes para a mesma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="5bd2d-108">A declaração para `MsgBox2` produz uma saída incorreta na caixa de mensagem porque o tipo de caractere, especificado como ANSI, é incompatível com o ponto de entrada `MessageBoxW`, que é o nome da função Unicode.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="5bd2d-109">A declaração `MsgBox3` cria uma incompatibilidade entre os campos **EntryPoint**, **CharSet** e **ExactSpelling**.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="5bd2d-110">Quando chamado, `MsgBox3` gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5bd2d-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="5bd2d-111">Para obter informações detalhadas sobre a nomeação de cadeia de caracteres e marshaling de nome, consulte [Especificando um conjunto de caracteres](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="5bd2d-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="5bd2d-112">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="5bd2d-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="5bd2d-113">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="5bd2d-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5bd2d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bd2d-114">See Also</span></span>  
 [<span data-ttu-id="5bd2d-115">Marshaling em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="5bd2d-115">Marshaling Strings</span></span>](marshaling-strings.md)  
 <span data-ttu-id="5bd2d-116">[Tipos de dados de invocação de plataforma](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5bd2d-116">[Platform Invoke Data Types](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))</span></span>  
 [<span data-ttu-id="5bd2d-117">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="5bd2d-117">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)  
 [<span data-ttu-id="5bd2d-118">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="5bd2d-118">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="5bd2d-119">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="5bd2d-119">Specifying a Character Set</span></span>](specifying-a-character-set.md)
