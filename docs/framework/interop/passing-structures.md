---
title: Passando estruturas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764916263f6f88615d61badaf2c32807bcc09b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-structures"></a><span data-ttu-id="a68e0-102">Passando estruturas</span><span class="sxs-lookup"><span data-stu-id="a68e0-102">Passing Structures</span></span>
<span data-ttu-id="a68e0-103">Muitas funções não gerenciadas esperam que você passe, como um parâmetro para a função, membros de estruturas (tipos definidos pelo usuário no Visual Basic) ou membros de classes que são definidas em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a68e0-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="a68e0-104">Ao passar estruturas ou classes para código não gerenciado usando invocação de plataforma, você deve fornecer informações adicionais para preservar o layout original e o alinhamento.</span><span class="sxs-lookup"><span data-stu-id="a68e0-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="a68e0-105">Este tópico apresenta o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>, que você usa para definir tipos formatados.</span><span class="sxs-lookup"><span data-stu-id="a68e0-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="a68e0-106">Para classes e estruturas gerenciadas, você pode selecionar vários comportamentos de layout previsível fornecidos pela enumeração **LayoutKind**.</span><span class="sxs-lookup"><span data-stu-id="a68e0-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="a68e0-107">Há uma diferença importante entre tipos de estrutura e classe que e central para os conceitos apresentados neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a68e0-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="a68e0-108">Estruturas são tipos de valor e classes são tipos de referência – classes sempre fornecem pelo menos um nível de indireção de memória (um ponteiro para um valor).</span><span class="sxs-lookup"><span data-stu-id="a68e0-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="a68e0-109">Essa diferença é importante porque funções não gerenciadas geralmente exigem indireção, conforme mostrado pelas assinaturas na primeira coluna da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a68e0-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="a68e0-110">A estrutura gerenciada e as declarações de classe nas colunas restantes mostram o grau em que você pode ajustar o nível de indireção na sua declaração. Declarações são fornecidas para o Visual Basic e Visual C#.</span><span class="sxs-lookup"><span data-stu-id="a68e0-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="a68e0-111">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="a68e0-111">Unmanaged signature</span></span>|<span data-ttu-id="a68e0-112">Declaração gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a68e0-112">Managed declaration:</span></span> <br /><span data-ttu-id="a68e0-113">sem indireção</span><span class="sxs-lookup"><span data-stu-id="a68e0-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="a68e0-114">Declaração gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a68e0-114">Managed declaration:</span></span> <br /><span data-ttu-id="a68e0-115">um nível de indireção</span><span class="sxs-lookup"><span data-stu-id="a68e0-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="a68e0-116">Demanda zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a68e0-117">Adiciona zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="a68e0-118">Não é possível porque já existe um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="a68e0-119">Demanda um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a68e0-120">Adiciona um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="a68e0-121">Adiciona zero níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="a68e0-122">Demanda dois níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="a68e0-123">Não é possível porque **ByRef** **ByRef** ou `ref` `ref` não pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="a68e0-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="a68e0-124">Adiciona um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="a68e0-125">A tabela descreve as diretrizes a seguir para declarações de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="a68e0-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="a68e0-126">Use uma estrutura passada por valor quando a função não gerenciada não demanda nenhuma indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="a68e0-127">Use uma estrutura passada por referência ou uma classe passada por valor quando a função não gerenciada demanda um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="a68e0-128">Use uma classe passada por referência quando a função não gerenciada demanda dois níveis de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="a68e0-129">Declarando e passando estruturas</span><span class="sxs-lookup"><span data-stu-id="a68e0-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="a68e0-130">O exemplo a seguir mostra como definir as estruturas `Point` e `Rect` em código gerenciado e passar tipos como parâmetro para a função **PtInRect** no arquivo User32.dll.</span><span class="sxs-lookup"><span data-stu-id="a68e0-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="a68e0-131">**PtInRect** tem a seguinte assinatura não gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a68e0-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="a68e0-132">Observe que você deve passar a estrutura Rect por referência, pois a função espera um ponteiro para um tipo RECT.</span><span class="sxs-lookup"><span data-stu-id="a68e0-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="a68e0-133">Declarando e passando classes</span><span class="sxs-lookup"><span data-stu-id="a68e0-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="a68e0-134">Você pode passar membros de uma classe para uma função de DLL não gerenciada, desde que a classe tenha um layout de membro fixo.</span><span class="sxs-lookup"><span data-stu-id="a68e0-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="a68e0-135">O exemplo a seguir demonstra como passar membros da classe `MySystemTime`, que são definidos em ordem sequencial, para o **GetSystemTime** no arquivo User32.dll.</span><span class="sxs-lookup"><span data-stu-id="a68e0-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="a68e0-136">**GetSystemTime** tem a seguinte assinatura não gerenciada:</span><span class="sxs-lookup"><span data-stu-id="a68e0-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="a68e0-137">Diferentemente dos tipos de valor, classes sempre têm pelo menos um nível de indireção.</span><span class="sxs-lookup"><span data-stu-id="a68e0-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a68e0-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a68e0-138">See Also</span></span>  
 [<span data-ttu-id="a68e0-139">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="a68e0-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
