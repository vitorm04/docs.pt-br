---
title: 'Como: Chamar uma função do Windows que use tipos não assinados'
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 5b78c808de4a16060d37844ad0f17e89fa6f6d84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548072"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="75445-102">Como chamar uma função do Windows que use tipos não assinados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75445-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="75445-103">Se você estiver consumindo uma classe, módulo ou estrutura que tem membros de tipos inteiros não assinados, poderá acessar esses membros com Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="75445-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="75445-104">Para chamar uma função do Windows que usa um tipo sem sinal</span><span class="sxs-lookup"><span data-stu-id="75445-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="75445-105">Use uma [instrução Declare](../../language-reference/statements/declare-statement.md) para informar Visual Basic qual biblioteca contém a função, qual nome está nessa biblioteca, qual é a sequência de chamada e como converter cadeias de caracteres ao chamá-la.</span><span class="sxs-lookup"><span data-stu-id="75445-105">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="75445-106">Na `Declare` instrução, use `UInteger` ,, `ULong` `UShort` ou `Byte` conforme apropriado para cada parâmetro com um tipo não assinado.</span><span class="sxs-lookup"><span data-stu-id="75445-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="75445-107">Consulte a documentação da função do Windows que você está chamando para localizar os nomes e valores das constantes que ele usa.</span><span class="sxs-lookup"><span data-stu-id="75445-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="75445-108">Muitos deles são definidos no arquivo WinUser. h.</span><span class="sxs-lookup"><span data-stu-id="75445-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="75445-109">Declare as constantes necessárias no seu código.</span><span class="sxs-lookup"><span data-stu-id="75445-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="75445-110">Muitas constantes do Windows são valores não assinados de 32 bits e você deve declará-los `As UInteger` .</span><span class="sxs-lookup"><span data-stu-id="75445-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="75445-111">Chame a função da maneira normal.</span><span class="sxs-lookup"><span data-stu-id="75445-111">Call the function in the normal way.</span></span> <span data-ttu-id="75445-112">O exemplo a seguir chama a função do Windows `MessageBox` , que usa um argumento inteiro sem sinal.</span><span class="sxs-lookup"><span data-stu-id="75445-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
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

     <span data-ttu-id="75445-113">Você pode testar a função `messageThroughWindows` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="75445-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="75445-114">Os `UInteger` tipos de dados,, e `ULong` não fazem `UShort` `SByte` parte da [independência de linguagem e dos componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), portanto, o código em conformidade com CLS não pode consumir um componente que os utilize.</span><span class="sxs-lookup"><span data-stu-id="75445-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="75445-115">Fazer uma chamada para código não gerenciado, como a API (interface de programação de aplicativo) do Windows, expõe seu código a possíveis riscos de segurança.</span><span class="sxs-lookup"><span data-stu-id="75445-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="75445-116">Chamar a API do Windows requer permissão de código não gerenciado, o que pode afetar sua execução em situações de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="75445-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="75445-117">Para obter mais informações, consulte <xref:System.Security.Permissions.SecurityPermission> e [permissões de acesso ao código](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="75445-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="75445-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="75445-118">See also</span></span>

- [<span data-ttu-id="75445-119">Data Types</span><span class="sxs-lookup"><span data-stu-id="75445-119">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="75445-120">Tipo de dados Integer</span><span class="sxs-lookup"><span data-stu-id="75445-120">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="75445-121">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="75445-121">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="75445-122">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="75445-122">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="75445-123">Passo a passo: Fazer chamadas de APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="75445-123">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
