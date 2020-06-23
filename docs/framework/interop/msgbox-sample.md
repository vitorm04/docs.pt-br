---
title: Exemplo de MsgBox
description: Veja um exemplo de passagem de tipos de cadeia de caracteres por valores como parâmetros usando MsgBox. Ele mostra quando usar os campos EntryPoint, CharSet e ExactSpelling no .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: ccf882e1f801dd18e5b65a4279fc580d927dd29d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904085"
---
# <a name="msgbox-sample"></a><span data-ttu-id="7ab14-104">Exemplo de MsgBox</span><span class="sxs-lookup"><span data-stu-id="7ab14-104">MsgBox Sample</span></span>
<span data-ttu-id="7ab14-105">Esta amostra demonstra como passar tipos de cadeia de caracteres por valor como parâmetros In e quando usar os campos <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> e <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="7ab14-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="7ab14-106">A amostra de MsgBox usa a seguinte função não gerenciada, mostrada com a respectiva declaração de função original:</span><span class="sxs-lookup"><span data-stu-id="7ab14-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="7ab14-107">**MessageBox** exportada de User32.dll.</span><span class="sxs-lookup"><span data-stu-id="7ab14-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="7ab14-108">Nesta amostra, a classe `NativeMethods` contém um protótipo gerenciado para cada função não gerenciada chamado pela classe `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="7ab14-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="7ab14-109">Os métodos de protótipo gerenciado `MsgBox`, `MsgBox2` e `MsgBox3` têm declarações diferentes para a mesma função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="7ab14-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="7ab14-110">A declaração para `MsgBox2` produz uma saída incorreta na caixa de mensagem porque o tipo de caractere, especificado como ANSI, é incompatível com o ponto de entrada `MessageBoxW`, que é o nome da função Unicode.</span><span class="sxs-lookup"><span data-stu-id="7ab14-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="7ab14-111">A declaração `MsgBox3` cria uma incompatibilidade entre os campos **EntryPoint**, **CharSet** e **ExactSpelling**.</span><span class="sxs-lookup"><span data-stu-id="7ab14-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="7ab14-112">Quando chamado, `MsgBox3` gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="7ab14-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="7ab14-113">Para obter informações detalhadas sobre a nomeação de cadeia de caracteres e marshaling de nome, consulte [Especificando um conjunto de caracteres](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="7ab14-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="7ab14-114">Declarando Protótipos</span><span class="sxs-lookup"><span data-stu-id="7ab14-114">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="7ab14-115">Chamando Funções</span><span class="sxs-lookup"><span data-stu-id="7ab14-115">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7ab14-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ab14-116">See also</span></span>

- [<span data-ttu-id="7ab14-117">Realizando marshaling de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7ab14-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="7ab14-118">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="7ab14-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="7ab14-119">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="7ab14-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="7ab14-120">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="7ab14-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
