---
title: "Como: chamar uma função do Windows que obtém tipos sem-sinal (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
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
ms.openlocfilehash: 7b6b1d46b6ccab0ec8d63fb8b7d8722b518b81b4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="61343-102">Como chamar uma função do Windows que use tipos não assinados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61343-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="61343-103">Se você está consumindo uma classe, módulo ou estrutura que possui membros dos tipos inteiros sem sinal, você pode acessar esses membros com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="61343-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="61343-104">Para chamar uma função do Windows que usa um tipo sem sinal</span><span class="sxs-lookup"><span data-stu-id="61343-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="61343-105">Use um [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) para informar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qual biblioteca contém a função, o que é o nome nessa biblioteca, o que é a sequência de chamada e como converter cadeias de caracteres para chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="61343-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="61343-106">No `Declare` instrução, use `UInteger`, `ULong`, `UShort`, ou `Byte` conforme apropriado para cada parâmetro com um tipo sem sinal.</span><span class="sxs-lookup"><span data-stu-id="61343-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="61343-107">Consulte a documentação para a função do Windows que você está chamando para localizar os nomes e valores de constantes que são usadas.</span><span class="sxs-lookup"><span data-stu-id="61343-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="61343-108">Muitas delas são definidas no arquivo WinUser. H.</span><span class="sxs-lookup"><span data-stu-id="61343-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="61343-109">Declare as constantes necessárias em seu código.</span><span class="sxs-lookup"><span data-stu-id="61343-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="61343-110">Muitas constantes do Windows são valores de 32 bits sem sinal, e você deve declarar essas `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="61343-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="61343-111">Chame a função da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="61343-111">Call the function in the normal way.</span></span> <span data-ttu-id="61343-112">O exemplo a seguir chama a função do Windows `MessageBox`, que usa um argumento de inteiro não assinado.</span><span class="sxs-lookup"><span data-stu-id="61343-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     <span data-ttu-id="61343-113">Você pode testar a função `messageThroughWindows` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="61343-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="61343-114">O `UInteger`, `ULong`, `UShort`, e `SByte` tipos de dados não são parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que os utiliza.</span><span class="sxs-lookup"><span data-stu-id="61343-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="61343-115">Fazer uma chamada para código não gerenciado, como a interface de programação de aplicativo (API) do Windows expõe seu código possíveis riscos de segurança.</span><span class="sxs-lookup"><span data-stu-id="61343-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="61343-116">Chamar a API do Windows requer permissão de código não gerenciado, que pode afetar sua execução em situações de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="61343-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="61343-117">Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission>e [permissões de acesso de código](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="61343-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61343-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61343-118">See Also</span></span>  
 <span data-ttu-id="61343-119">[Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="61343-119">[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="61343-120"> [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="61343-120"> [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="61343-121"> [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="61343-121"> [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) </span></span>  
<span data-ttu-id="61343-122"> [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="61343-122"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="61343-123"> [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span><span class="sxs-lookup"><span data-stu-id="61343-123"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)</span></span>
