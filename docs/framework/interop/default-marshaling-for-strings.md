---
title: Marshaling padrão para cadeias de caracteres
description: Examine o comportamento de marshaling padrão para cadeias de caracteres em interfaces, invocação de plataforma, estruturas, & buffers de cadeia de comprimento fixo no .NET.
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
ms.openlocfilehash: 81df2dcc132c8ce057fa3e0e7d0ad04832f7a48b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555049"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="e2425-103">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e2425-103">Default Marshaling for Strings</span></span>

<span data-ttu-id="e2425-104">As classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> têm comportamentos de marshaling semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e2425-104">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="e2425-105">As cadeias de caracteres têm o marshaling realizado como um tipo `BSTR` de estilo COM ou como uma cadeia de caracteres terminada em nulo (uma matriz de caracteres que termina com um caractere nulo).</span><span class="sxs-lookup"><span data-stu-id="e2425-105">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="e2425-106">Os caracteres na cadeia de caracteres podem ter o marshaling realizado como Unicode (o padrão em sistemas Windows) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="e2425-106">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="e2425-107">Cadeias de caracteres usadas em interfaces</span><span class="sxs-lookup"><span data-stu-id="e2425-107">Strings Used in Interfaces</span></span>

<span data-ttu-id="e2425-108">A tabela a seguir mostra as opções de marshaling para o tipo de dados String ao realizar marshaling dele como um argumento de método para um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e2425-108">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="e2425-109">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres para interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="e2425-109">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="e2425-110">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="e2425-110">Enumeration type</span></span>|<span data-ttu-id="e2425-111">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="e2425-111">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="e2425-112">`UnmanagedType.BStr` (padrão)</span><span class="sxs-lookup"><span data-stu-id="e2425-112">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="e2425-113">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2425-113">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="e2425-114">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-114">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="e2425-115">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-115">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="e2425-116">Esta tabela aplica-se a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e2425-116">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="e2425-117">Para <xref:System.Text.StringBuilder>, as únicas opções permitidas são `UnmanagedType.LPStr` e `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="e2425-117">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="e2425-118">O exemplo a seguir mostra as cadeias de caracteres declaradas na interface `IStringWorker`.</span><span class="sxs-lookup"><span data-stu-id="e2425-118">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="e2425-119">O exemplo a seguir mostra a interface correspondente descrita em uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="e2425-119">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="e2425-120">Cadeias de caracteres usadas na invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="e2425-120">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="e2425-121">A invocação de plataforma copia argumentos de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado da plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-121">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="e2425-122">As cadeias de caracteres são imutáveis e não são copiadas novamente da memória não gerenciada para a memória gerenciada quando a chamada é retornada.</span><span class="sxs-lookup"><span data-stu-id="e2425-122">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="e2425-123">A tabela a seguir lista as opções de marshaling para cadeias de caracteres ao realizar marshaling delas como um argumento de método de uma chamada de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-123">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="e2425-124">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e2425-124">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="e2425-125">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="e2425-125">Enumeration type</span></span>|<span data-ttu-id="e2425-126">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="e2425-126">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="e2425-127">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="e2425-127">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="e2425-128">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2425-128">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="e2425-129">`UnmanagedType.LPStr` (padrão)</span><span class="sxs-lookup"><span data-stu-id="e2425-129">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="e2425-130">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-130">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="e2425-131">Um ponteiro para uma matriz terminada em nulo de caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-131">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="e2425-132">Um ponteiro para uma matriz terminada em nulo de caracteres codificados em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e2425-132">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="e2425-133">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-133">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="e2425-134">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-134">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="e2425-135">Um valor que permite que o Visual Basic .NET altere uma cadeia de caracteres no código não gerenciado, refletindo os resultados no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e2425-135">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="e2425-136">Há suporte para esse valor apenas na invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-136">This value is supported only for platform invoke.</span></span> <span data-ttu-id="e2425-137">Esse é o valor padrão no Visual Basic para cadeias de caracteres `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="e2425-137">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="e2425-138">Esta tabela aplica-se a <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e2425-138">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="e2425-139">Para <xref:System.Text.StringBuilder>, as únicas opções permitidas são `LPStr`, `LPTStr` e `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="e2425-139">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="e2425-140">A definição de tipo a seguir mostra o uso correto de `MarshalAsAttribute` para chamadas de invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-140">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="e2425-141">Cadeias de caracteres usadas em estruturas</span><span class="sxs-lookup"><span data-stu-id="e2425-141">Strings Used in Structures</span></span>

<span data-ttu-id="e2425-142">Cadeias de caracteres são membros válidos de estruturas; no entanto, buffers do <xref:System.Text.StringBuilder> são inválidos em estruturas.</span><span class="sxs-lookup"><span data-stu-id="e2425-142">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="e2425-143">A tabela a seguir mostra as opções de marshaling para o <xref:System.String> quando o tipo de dados é empacotado como um campo.</span><span class="sxs-lookup"><span data-stu-id="e2425-143">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="e2425-144">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de cadeias de caracteres para um campo.</span><span class="sxs-lookup"><span data-stu-id="e2425-144">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="e2425-145">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="e2425-145">Enumeration type</span></span>|<span data-ttu-id="e2425-146">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="e2425-146">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="e2425-147">Um `BSTR` de estilo COM com um tamanho prefixado e caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2425-147">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="e2425-148">`UnmanagedType.LPStr` (padrão)</span><span class="sxs-lookup"><span data-stu-id="e2425-148">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="e2425-149">Um ponteiro para uma matriz de caracteres ANSI terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-149">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="e2425-150">Um ponteiro para uma matriz terminada em nulo de caracteres dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-150">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="e2425-151">Um ponteiro para uma matriz terminada em nulo de caracteres codificados em UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e2425-151">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="e2425-152">Um ponteiro para uma matriz de caracteres Unicode terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="e2425-152">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="e2425-153">Uma matriz de comprimento fixo de caracteres; o tipo da matriz é determinado pelo conjunto de caracteres da estrutura que o contém.</span><span class="sxs-lookup"><span data-stu-id="e2425-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="e2425-154">O tipo `ByValTStr` é usado para matrizes de caracteres embutidas e de comprimento fixo que aparecem em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="e2425-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="e2425-155">Outros tipos aplicam as referências de cadeia de caracteres contidas em estruturas que contêm ponteiros para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e2425-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="e2425-156">O argumento `CharSet` do <xref:System.Runtime.InteropServices.StructLayoutAttribute> que é aplicado à estrutura recipiente determina o formato do caractere de cadeias de caracteres em estruturas.</span><span class="sxs-lookup"><span data-stu-id="e2425-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="e2425-157">As estruturas de exemplo a seguir contêm referências de cadeia de caracteres e cadeias de caracteres embutidas, bem como caracteres ANSI, Unicode e dependentes de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e2425-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="e2425-158">A representação dessas estruturas em uma biblioteca de tipos é mostrada no código C++ a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2425-158">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="e2425-159">O exemplo a seguir mostra como usar o <xref:System.Runtime.InteropServices.MarshalAsAttribute> para definir a mesma estrutura em formatos diferentes.</span><span class="sxs-lookup"><span data-stu-id="e2425-159">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="e2425-160">Buffers de cadeia de caracteres de comprimento fixo</span><span class="sxs-lookup"><span data-stu-id="e2425-160">Fixed-Length String Buffers</span></span>

<span data-ttu-id="e2425-161">Em algumas circunstâncias, um buffer de caracteres de comprimento fixo deve ser passado para um código não gerenciado para ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="e2425-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="e2425-162">Apenas passar uma cadeia de caracteres não funciona neste caso, porque o receptor não pode modificar o conteúdo do buffer passado.</span><span class="sxs-lookup"><span data-stu-id="e2425-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="e2425-163">Mesmo se a cadeia de caracteres for passada por referência, não haverá nenhuma maneira de inicializar o buffer em determinado tamanho.</span><span class="sxs-lookup"><span data-stu-id="e2425-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="e2425-164">A solução é passar um buffer <xref:System.Text.StringBuilder> como o argumento em vez de um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e2425-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="e2425-165">Um `StringBuilder` pode ser desreferenciado e modificado pelo receptor, desde que ele não exceda a capacidade do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e2425-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="e2425-166">Ele também pode ser inicializado com um comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="e2425-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="e2425-167">Por exemplo, se você inicializar um buffer do `StringBuilder` em uma capacidade de `N`, o marshaler fornecerá um buffer com o tamanho de (`N`+ 1) caracteres.</span><span class="sxs-lookup"><span data-stu-id="e2425-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="e2425-168">O + 1 leva em conta o fato de que a cadeia de caracteres não gerenciada tem um terminador nulo, ao contrário de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e2425-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="e2425-169">Por exemplo, a função de API do Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) (definida em *WinUser. h*) requer que o chamador passe um buffer de caracteres de comprimento fixo para o qual a função grava o texto da janela.</span><span class="sxs-lookup"><span data-stu-id="e2425-169">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="e2425-170">`LpString` aponta para um buffer alocado pelo chamador com o tamanho `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="e2425-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="e2425-171">O chamador deve alocar o buffer e definir o argumento `nMaxCount` com o tamanho do buffer alocado.</span><span class="sxs-lookup"><span data-stu-id="e2425-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="e2425-172">O exemplo a seguir mostra a declaração de função `GetWindowText`, conforme definida em *winuser.h*.</span><span class="sxs-lookup"><span data-stu-id="e2425-172">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="e2425-173">Um `StringBuilder` pode ser desreferenciado e modificado pelo receptor, desde que ele não exceda a capacidade do `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e2425-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="e2425-174">O exemplo de código a seguir demonstra como `StringBuilder` pode ser inicializado com um comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="e2425-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="e2425-175">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2425-175">See also</span></span>

- [<span data-ttu-id="e2425-176">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="e2425-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="e2425-177">Realizando marshaling de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e2425-177">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="e2425-178">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="e2425-178">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="e2425-179">[Atributos direcionais](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e2425-179">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="e2425-180">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="e2425-180">Copying and Pinning</span></span>](copying-and-pinning.md)
