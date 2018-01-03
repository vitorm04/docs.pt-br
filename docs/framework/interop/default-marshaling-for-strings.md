---
title: "Marshaling padrão para cadeias de caracteres"
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
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8de04f9674e67bf1498fb8f25f2b3c61fec438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="009e0-102">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="009e0-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="009e0-103">As classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> têm comportamentos de marshaling semelhantes.</span><span class="sxs-lookup"><span data-stu-id="009e0-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="009e0-104">As cadeias de caracteres têm o marshaling realizado como um tipo `BSTR` de estilo COM ou como uma cadeia de caracteres terminada em nulo (uma matriz de caracteres que termina com um caractere nulo).</span><span class="sxs-lookup"><span data-stu-id="009e0-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="009e0-105">Os caracteres na cadeia de caracteres podem ter o marshaling realizado como Unicode (o padrão em sistemas Windows) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="009e0-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="009e0-106">Este tópico fornece as seguintes informações sobre o marshaling de tipos de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="009e0-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="009e0-107">Cadeias de caracteres usadas em interfaces</span><span class="sxs-lookup"><span data-stu-id="009e0-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="009e0-108">Cadeias de caracteres usadas na invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="009e0-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="009e0-109">Cadeias de caracteres usadas em estruturas</span><span class="sxs-lookup"><span data-stu-id="009e0-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="009e0-110">Buffers de cadeia de caracteres de comprimento fixo</span><span class="sxs-lookup"><span data-stu-id="009e0-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>   
## <a name="strings-used-in-interfaces"></a><span data-ttu-id="009e0-111">Cadeias de caracteres usadas em interfaces</span><span class="sxs-lookup"><span data-stu-id="009e0-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="009e0-112">A tabela a seguir mostra as opções de marshaling para o tipo de dados String ao realizar marshaling dele como um argumento de método para um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="009e0-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="009e0-113">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres para interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="009e0-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="009e0-114">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="009e0-114">Enumeration type</span></span>|<span data-ttu-id="009e0-115">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="009e0-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="009e0-116">`UnmanagedType.BStr` (padrão)</span><span class="sxs-lookup"><span data-stu-id="009e0-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="009e0-117">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="009e0-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="009e0-118">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="009e0-119">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="009e0-120">Esta tabela se aplica a cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-120">This table applies to strings.</span></span> <span data-ttu-id="009e0-121">No entanto, para o <xref:System.Text.StringBuilder>, as únicas opções permitidas são `UnmanagedType.LPStr` e `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="009e0-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="009e0-122">O exemplo a seguir mostra as cadeias de caracteres declaradas na interface `IStringWorker`.</span><span class="sxs-lookup"><span data-stu-id="009e0-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);  
```  
  
 <span data-ttu-id="009e0-123">O exemplo a seguir mostra a interface correspondente descrita em uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="009e0-123">The following example shows the corresponding interface described in a type library.</span></span>  
  
```  
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor5"></a>   
## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="009e0-124">Cadeias de caracteres usadas na invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="009e0-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="009e0-125">A invocação de plataforma copia argumentos de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado da plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="009e0-126">As cadeias de caracteres são imutáveis e não são copiadas novamente da memória não gerenciada para a memória gerenciada quando a chamada é retornada.</span><span class="sxs-lookup"><span data-stu-id="009e0-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="009e0-127">A tabela a seguir lista as opções de marshaling para cadeias de caracteres ao realizar marshaling delas como um argumento de método de uma chamada de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="009e0-128">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="009e0-129">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="009e0-129">Enumeration type</span></span>|<span data-ttu-id="009e0-130">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="009e0-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="009e0-131">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="009e0-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="009e0-132">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="009e0-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="009e0-133">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="009e0-134">Um ponteiro para uma matriz terminada em nulo de caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="009e0-135">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="009e0-136">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="009e0-137">Um valor que permite que o .NET do Visual Basic altere uma cadeia de caracteres no código não gerenciado e reflita os resultados no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="009e0-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="009e0-138">Há suporte para esse valor apenas na invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="009e0-139">Esse é o valor padrão no Visual Basic para cadeias de caracteres `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="009e0-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="009e0-140">Esta tabela se aplica a cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-140">This table applies to strings.</span></span> <span data-ttu-id="009e0-141">No entanto, para o <xref:System.Text.StringBuilder>, as únicas opções permitidas são `LPStr`, `LPTStr` e `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="009e0-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="009e0-142">A definição de tipo a seguir mostra o uso correto de `MarshalAsAttribute` para chamadas de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```  
  
```csharp  
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a><span data-ttu-id="009e0-143">Cadeias de caracteres usadas em estruturas</span><span class="sxs-lookup"><span data-stu-id="009e0-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="009e0-144">Cadeias de caracteres são membros válidos de estruturas; no entanto, buffers do <xref:System.Text.StringBuilder> são inválidos em estruturas.</span><span class="sxs-lookup"><span data-stu-id="009e0-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="009e0-145">A tabela a seguir mostra as opções de marshaling para o tipo de dados String quando o tipo tem o marshaling realizado como um campo.</span><span class="sxs-lookup"><span data-stu-id="009e0-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="009e0-146">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres para um campo.</span><span class="sxs-lookup"><span data-stu-id="009e0-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="009e0-147">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="009e0-147">Enumeration type</span></span>|<span data-ttu-id="009e0-148">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="009e0-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="009e0-149">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="009e0-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="009e0-150">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="009e0-151">Um ponteiro para uma matriz terminada em nulo de caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="009e0-152">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="009e0-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="009e0-153">Uma matriz de comprimento fixo de caracteres; o tipo da matriz é determinado pelo conjunto de caracteres da estrutura que o contém.</span><span class="sxs-lookup"><span data-stu-id="009e0-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="009e0-154">O tipo `ByValTStr` é usado para matrizes de caracteres embutidas e de comprimento fixo que aparecem em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="009e0-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="009e0-155">Outros tipos aplicam as referências de cadeia de caracteres contidas em estruturas que contêm ponteiros para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="009e0-156">O argumento `CharSet` do atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> aplicado à estrutura que o contém determina o formato do caractere de cadeias de caracteres em estruturas.</span><span class="sxs-lookup"><span data-stu-id="009e0-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="009e0-157">As estruturas de exemplo a seguir contêm referências de cadeia de caracteres e cadeias de caracteres embutidas, bem como caracteres ANSI, Unicode e dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="009e0-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="009e0-158">Representação da Biblioteca de Tipos</span><span class="sxs-lookup"><span data-stu-id="009e0-158">Type Library Representation</span></span>  
  
```  
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 <span data-ttu-id="009e0-159">O exemplo de código a seguir mostra como usar o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para definir a mesma estrutura em formatos diferentes.</span><span class="sxs-lookup"><span data-stu-id="009e0-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="009e0-160">Buffers de cadeia de caracteres de comprimento fixo</span><span class="sxs-lookup"><span data-stu-id="009e0-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="009e0-161">Em algumas circunstâncias, um buffer de caracteres de comprimento fixo deve ser passado para um código não gerenciado para ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="009e0-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="009e0-162">Apenas passar uma cadeia de caracteres não funciona neste caso, porque o receptor não pode modificar o conteúdo do buffer passado.</span><span class="sxs-lookup"><span data-stu-id="009e0-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="009e0-163">Mesmo se a cadeia de caracteres for passada por referência, não haverá nenhuma maneira de inicializar o buffer em determinado tamanho.</span><span class="sxs-lookup"><span data-stu-id="009e0-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="009e0-164">A solução é passar um buffer do <xref:System.Text.StringBuilder> como argumento, em vez de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="009e0-165">Um `StringBuilder` pode ser desreferenciado e modificado pelo receptor, desde que ele não exceda a capacidade do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="009e0-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="009e0-166">Ele também pode ser inicializado com um comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="009e0-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="009e0-167">Por exemplo, se você inicializar um buffer do `StringBuilder` em uma capacidade de `N`, o marshaler fornecerá um buffer com o tamanho de (`N`+ 1) caracteres.</span><span class="sxs-lookup"><span data-stu-id="009e0-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="009e0-168">O + 1 leva em conta o fato de que a cadeia de caracteres não gerenciada tem um terminador nulo, ao contrário de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="009e0-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="009e0-169">Por exemplo, a função `GetWindowText` da API do Microsoft Win32 (definida em Windows.h) é um buffer de caracteres de comprimento fixo que deve ser passada para um código não gerenciado para ser manipulada.</span><span class="sxs-lookup"><span data-stu-id="009e0-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="009e0-170">`LpString` aponta para um buffer alocado pelo chamador com o tamanho `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="009e0-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="009e0-171">O chamador deve alocar o buffer e definir o argumento `nMaxCount` com o tamanho do buffer alocado.</span><span class="sxs-lookup"><span data-stu-id="009e0-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="009e0-172">O código a seguir mostra a declaração da função `GetWindowText`, conforme definido em Windows.h.</span><span class="sxs-lookup"><span data-stu-id="009e0-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="009e0-173">Um `StringBuilder` pode ser desreferenciado e modificado pelo receptor, desde que ele não exceda a capacidade do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="009e0-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="009e0-174">O exemplo de código a seguir demonstra como `StringBuilder` pode ser inicializado com um comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="009e0-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="009e0-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="009e0-175">See Also</span></span>  
 [<span data-ttu-id="009e0-176">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="009e0-176">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [<span data-ttu-id="009e0-177">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="009e0-177">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="009e0-178">Atributos direcionais</span><span class="sxs-lookup"><span data-stu-id="009e0-178">Directional Attributes</span></span>](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [<span data-ttu-id="009e0-179">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="009e0-179">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)
