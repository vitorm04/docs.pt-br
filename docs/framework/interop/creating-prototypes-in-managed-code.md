---
title: "Criando protótipos em código gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9a3dcc625a838dc8823930e31541543b9c4c7f8f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="b0988-102">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="b0988-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="b0988-103">Este tópico descreve como acessar funções não gerenciadas e apresenta vários campos de atributo que anotam a definição de método no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b0988-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="b0988-104">Para obter exemplos que demonstram como construir declarações baseadas no .NET a serem usadas com a invocação de plataforma, consulte [Realizando marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="b0988-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="b0988-105">Antes de poder acessar uma função de DLL não gerenciada no código gerenciado, você precisa saber o nome da função e o nome da DLL que a exporta.</span><span class="sxs-lookup"><span data-stu-id="b0988-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="b0988-106">Com essas informações, você pode começar a escrever a definição gerenciada para uma função não gerenciada que é implementada em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="b0988-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="b0988-107">Além disso, você pode ajustar a maneira como essa invocação de plataforma cria a função e realiza marshaling dos dados bidirecionalmente na função.</span><span class="sxs-lookup"><span data-stu-id="b0988-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0988-108">As funções de API do Win32 que alocam uma cadeia de caracteres permitem liberar a cadeia de caracteres usando um método como `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="b0988-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="b0988-109">A invocação de plataforma manipula esses parâmetros de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="b0988-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="b0988-110">Para chamadas de invocação de plataforma, torne o parâmetro um tipo `IntPtr`, em vez de um tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="b0988-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="b0988-111">Use métodos que são fornecidos pela classe <xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName> para converter o tipo em uma cadeia de caracteres manualmente e libere-a manualmente.</span><span class="sxs-lookup"><span data-stu-id="b0988-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="b0988-112">Noções básicas sobre a declaração</span><span class="sxs-lookup"><span data-stu-id="b0988-112">Declaration Basics</span></span>  
 <span data-ttu-id="b0988-113">As definições gerenciadas para funções não gerenciadas são dependentes de idioma, como é possível ver nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0988-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="b0988-114">Para obter exemplos de código mais completos, consulte [Exemplos de invocação de plataforma](../../../docs/framework/interop/platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="b0988-114">For more complete code examples, see [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="b0988-115">Para aplicar os campos <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> ou <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> a uma declaração [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], use o atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, em vez da instrução `Declare`.</span><span class="sxs-lookup"><span data-stu-id="b0988-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="b0988-116">Ajustando a definição</span><span class="sxs-lookup"><span data-stu-id="b0988-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="b0988-117">Independentemente de você defini-los explicitamente ou não, os campos de atributo estão trabalhando, definindo o comportamento do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b0988-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="b0988-118">A invocação de plataforma funciona de acordo com os valores padrão definidos em vários campos que existem como metadados em um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0988-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="b0988-119">Altere esse comportamento padrão ajustando os valores de um ou mais campos.</span><span class="sxs-lookup"><span data-stu-id="b0988-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="b0988-120">Em muitos casos, use o <xref:System.Runtime.InteropServices.DllImportAttribute> para definir um valor.</span><span class="sxs-lookup"><span data-stu-id="b0988-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="b0988-121">A tabela a seguir lista o conjunto completo de campos de atributo que pertencem à invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b0988-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="b0988-122">Para cada campo, a tabela inclui o valor padrão e um link para informações sobre como usar esses campos para definir funções de DLL não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="b0988-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="b0988-123">Campo</span><span class="sxs-lookup"><span data-stu-id="b0988-123">Field</span></span>|<span data-ttu-id="b0988-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0988-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="b0988-125">Habilita ou desabilita o mapeamento de melhor ajuste.</span><span class="sxs-lookup"><span data-stu-id="b0988-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="b0988-126">Especifica a convenção de chamada a ser usada ao passar argumentos de método.</span><span class="sxs-lookup"><span data-stu-id="b0988-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="b0988-127">O padrão é `WinAPI`, que corresponde a `__stdcall` nas plataformas Intel de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b0988-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="b0988-128">Controla a desconfiguração de nome e a maneira como os argumentos de cadeia de caracteres devem ter o marshaling realizado para a função.</span><span class="sxs-lookup"><span data-stu-id="b0988-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="b0988-129">O padrão é `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="b0988-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="b0988-130">Especifica o ponto de entrada de DLL a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="b0988-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="b0988-131">Controla se um ponto de entrada deve ser modificado para que ele corresponda ao conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b0988-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="b0988-132">O valor padrão varia de acordo com a linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="b0988-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="b0988-133">Controla se a assinatura de método gerenciada deve ser transformada em uma assinatura não gerenciada que retorna um HRESULT e que tem um argumento adicional [out, retval] para o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="b0988-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="b0988-134">O padrão é `true` (a assinatura não deve ser transformada).</span><span class="sxs-lookup"><span data-stu-id="b0988-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="b0988-135">Permite ao chamador usar a função de API `Marshal.GetLastWin32Error` para determinar se ocorreu um erro ao executar o método.</span><span class="sxs-lookup"><span data-stu-id="b0988-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="b0988-136">No Visual Basic, o padrão é `true`; no C# e no C++, o padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="b0988-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="b0988-137">Controla a geração de uma exceção em um caractere Unicode não mapeável que é convertido em um caractere “?” ANSI.</span><span class="sxs-lookup"><span data-stu-id="b0988-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="b0988-138">Para obter informações detalhadas sobre a referência, consulte <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0988-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="b0988-139">Considerações sobre segurança da invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="b0988-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="b0988-140">Os membros `Assert`, `Deny` e `PermitOnly` da enumeração <xref:System.Security.Permissions.SecurityAction> são chamados de *modificadores de movimentação de pilha*.</span><span class="sxs-lookup"><span data-stu-id="b0988-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="b0988-141">Esses membros serão ignorados se forem usados como atributos declarativos em declarações da invocação de plataforma e em instruções COM da linguagem IDL.</span><span class="sxs-lookup"><span data-stu-id="b0988-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="b0988-142">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="b0988-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="b0988-143">As amostras de invocação de plataforma desta seção ilustram o uso do atributo `RegistryPermission` com os modificadores de movimentação de pilha.</span><span class="sxs-lookup"><span data-stu-id="b0988-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="b0988-144">No exemplo de código a seguir, os modificadores <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny` e `PermitOnly` são ignorados.</span><span class="sxs-lookup"><span data-stu-id="b0988-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="b0988-145">No entanto, o modificador `Demand` no exemplo a seguir é aceito.</span><span class="sxs-lookup"><span data-stu-id="b0988-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="b0988-146">Os modificadores <xref:System.Security.Permissions.SecurityAction> funcionam corretamente se são colocados em uma classe que contém (encapsula) a chamada da invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b0988-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="b0988-147">Os modificadores <xref:System.Security.Permissions.SecurityAction> também funcionam corretamente em um cenário aninhado em que são colocados no chamador da chamada de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="b0988-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="b0988-148">Exemplos de interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="b0988-148">COM Interop Examples</span></span>  
 <span data-ttu-id="b0988-149">As amostras de interoperabilidade COM desta seção ilustram o uso do atributo `RegistryPermission` com os modificadores de movimentação de pilha.</span><span class="sxs-lookup"><span data-stu-id="b0988-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="b0988-150">As declarações da interface de interoperabilidade COM a seguir ignoram os modificadores `Assert`, `Deny` e `PermitOnly`, da mesma forma que os exemplos da invocação de plataforma da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="b0988-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="b0988-151">Além disso, o modificador `Demand` não é aceito em cenários de declaração da interface de interoperabilidade COM, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b0988-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0988-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0988-152">See Also</span></span>  
 <span data-ttu-id="b0988-153">[Consumindo funções de DLL não gerenciadas](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-153">[Consuming Unmanaged DLL Functions](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md) </span></span>  
 <span data-ttu-id="b0988-154">[Especificando um ponto de entrada](../../../docs/framework/interop/specifying-an-entry-point.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-154">[Specifying an Entry Point](../../../docs/framework/interop/specifying-an-entry-point.md) </span></span>  
 <span data-ttu-id="b0988-155">[Especificando um conjunto de caracteres](../../../docs/framework/interop/specifying-a-character-set.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-155">[Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md) </span></span>  
 <span data-ttu-id="b0988-156">[Exemplos de invocação de plataforma](../../../docs/framework/interop/platform-invoke-examples.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-156">[Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md) </span></span>  
 <span data-ttu-id="b0988-157">[Considerações sobre Segurança da Invocação de Plataforma](http://msdn.microsoft.com/en-us/bbcc67f7-50b5-4917-88ed-cb15470409fb) </span><span class="sxs-lookup"><span data-stu-id="b0988-157">[Platform Invoke Security Considerations](http://msdn.microsoft.com/en-us/bbcc67f7-50b5-4917-88ed-cb15470409fb) </span></span>  
 <span data-ttu-id="b0988-158">[Identificando funções em DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-158">[Identifying Functions in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md) </span></span>  
 <span data-ttu-id="b0988-159">[Criando uma classe para conter funções de DLL](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md) </span><span class="sxs-lookup"><span data-stu-id="b0988-159">[Creating a Class to Hold DLL Functions](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md) </span></span>  
 [<span data-ttu-id="b0988-160">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="b0988-160">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)

