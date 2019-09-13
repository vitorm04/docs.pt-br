---
title: Personalização do marshaling de estrutura – .NET
description: Saiba como personalizar a forma como o .NET realiza marshal em suas estruturas para uma representação nativa.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b174a817e82f9a9f123c79581656cc8e7179b435
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929034"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="29df9-103">Personalização do marshaling de estrutura</span><span class="sxs-lookup"><span data-stu-id="29df9-103">Customizing structure marshaling</span></span>

<span data-ttu-id="29df9-104">Às vezes, as regras de marshaling padrão para estruturas não são exatamente o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="29df9-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="29df9-105">Os tempos de execução do .NET fornecem alguns pontos de extensão para você personalizar o layout de sua estrutura e como os campos têm o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="29df9-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="29df9-106">Personalização do layout de estrutura</span><span class="sxs-lookup"><span data-stu-id="29df9-106">Customizing structure layout</span></span>

<span data-ttu-id="29df9-107">O .NET fornece o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> e a enumeração <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> para permitir que você personalize como os campos são colocados na memória.</span><span class="sxs-lookup"><span data-stu-id="29df9-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="29df9-108">As diretrizes a seguir ajudarão a evitar problemas comuns.</span><span class="sxs-lookup"><span data-stu-id="29df9-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="29df9-109">**✔️ CONSIDERE** usar `LayoutKind.Sequential` sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="29df9-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="29df9-110">**✔️ USE** somente `LayoutKind.Explicit` no marshaling quando seu struct nativo também tiver um layout explícito, como uma união.</span><span class="sxs-lookup"><span data-stu-id="29df9-110">**✔️ DO** only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="29df9-111">**❌ EVITE** usar `LayoutKind.Explicit` ao realizar marshaling de estruturas em plataformas que não sejam Windows.</span><span class="sxs-lookup"><span data-stu-id="29df9-111">**❌ AVOID** using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms.</span></span> <span data-ttu-id="29df9-112">O tempo de execução do .NET Core não dá suporte à passagem de estruturas explícitas por valor para funções nativas em sistemas Intel ou AMD de 64 bits que não sejam Windows.</span><span class="sxs-lookup"><span data-stu-id="29df9-112">The .NET Core runtime doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="29df9-113">No entanto, o tempo de execução dá suporte à passagem de estruturas explícitas por referência em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="29df9-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="29df9-114">Personalização do marshaling de campo booliano</span><span class="sxs-lookup"><span data-stu-id="29df9-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="29df9-115">O código nativo tem muitas representações boolianas diferentes.</span><span class="sxs-lookup"><span data-stu-id="29df9-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="29df9-116">Somente no Windows, há três formas de representar valores boolianos.</span><span class="sxs-lookup"><span data-stu-id="29df9-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="29df9-117">O tempo de execução não conhece a definição nativa de sua estrutura, portanto, o melhor que ele pode fazer é estimar como realizar marshal de seus valores boolianos.</span><span class="sxs-lookup"><span data-stu-id="29df9-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="29df9-118">O tempo de execução do .NET fornece uma maneira de indicar como realizar marshal de seu campo booliano.</span><span class="sxs-lookup"><span data-stu-id="29df9-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="29df9-119">Os exemplos a seguir mostram como realizar marshal do .NET `bool` para diferentes tipos boolianos nativos.</span><span class="sxs-lookup"><span data-stu-id="29df9-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="29df9-120">Valores boolianos padrão para realizar marshaling como um valor [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) Win32 nativo de 4 bytes conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="29df9-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="29df9-121">Se você quiser ser explícito, use o valor <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> para obter o mesmo comportamento descrito acima:</span><span class="sxs-lookup"><span data-stu-id="29df9-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

<span data-ttu-id="29df9-122">Usando os valores `UnmanagedType.U1` ou `UnmanagedType.I1` abaixo, você pode informar o tempo de execução para realizar marshal do campo `b` como um tipo `bool` nativo de 1 byte.</span><span class="sxs-lookup"><span data-stu-id="29df9-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

<span data-ttu-id="29df9-123">No Windows, use o valor <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> para informar o tempo de execução para realizar marshal de seu valor booliano em um valor `VARIANT_BOOL` de 2 bytes:</span><span class="sxs-lookup"><span data-stu-id="29df9-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> <span data-ttu-id="29df9-124">`VARIANT_BOOL` é diferente da maioria dos tipos de bool em que `VARIANT_TRUE = -1` e `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="29df9-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="29df9-125">Além disso, todos os valores que não são iguais a `VARIANT_TRUE` são considerados falsos.</span><span class="sxs-lookup"><span data-stu-id="29df9-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="29df9-126">Personalização do marshaling de campo de matriz</span><span class="sxs-lookup"><span data-stu-id="29df9-126">Customizing array field marshaling</span></span>

<span data-ttu-id="29df9-127">O .NET também inclui algumas formas de personalizar o marshaling de matriz.</span><span class="sxs-lookup"><span data-stu-id="29df9-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="29df9-128">Por padrão, o .NET realiza marshal de matrizes como um ponteiro para uma lista contígua dos elementos:</span><span class="sxs-lookup"><span data-stu-id="29df9-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

<span data-ttu-id="29df9-129">Se você estiver interagindo com APIs COM, talvez seja necessário realizar marshal de matrizes como objetos `SAFEARRAY*`.</span><span class="sxs-lookup"><span data-stu-id="29df9-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="29df9-130">Use o valor <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> e <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> para informar o tempo de execução para realizar marshal de uma matriz como uma `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="29df9-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

<span data-ttu-id="29df9-131">Se for necessário personalizar o tipo de elemento que está na `SAFEARRAY`, use os campos <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> e <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> para personalizar o tipo de elemento exato da `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="29df9-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="29df9-132">Se você precisar realizar marshal da matriz in-loco, use o valor <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> para informar o marshaler para realizar marshal da matriz in-loco.</span><span class="sxs-lookup"><span data-stu-id="29df9-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="29df9-133">Ao usar esse marshaling, você também precisa fornecer um valor ao campo <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> para o número de elementos na matriz, para que o tempo de execução possa alocar espaço corretamente para a estrutura.</span><span class="sxs-lookup"><span data-stu-id="29df9-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> <span data-ttu-id="29df9-134">O .NET não dá suporte à realização de marshaling de um campo de matriz de comprimento variável como um Membro de Matriz Flexível C99.</span><span class="sxs-lookup"><span data-stu-id="29df9-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="29df9-135">Personalização do marshaling de campo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="29df9-135">Customizing string field marshaling</span></span>

<span data-ttu-id="29df9-136">O .NET também fornece uma ampla variedade de personalizações para realizar marshaling de campos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="29df9-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="29df9-137">Por padrão, o .NET realiza marshal de uma cadeia de caracteres como um ponteiro para uma cadeia de caracteres terminada em nulo.</span><span class="sxs-lookup"><span data-stu-id="29df9-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="29df9-138">A codificação depende do valor do campo <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> no <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="29df9-139">Se nenhum atributo for especificado, a codificação será padronizada para uma codificação ANSI.</span><span class="sxs-lookup"><span data-stu-id="29df9-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="29df9-140">Se você precisar usar codificações diferentes para campos distintos ou apenas prefere ser mais explícito em sua definição de struct, use os valores <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> em um atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

<span data-ttu-id="29df9-141">Se quiser realizar marshal de suas cadeias de caracteres usando a codificação UTF-8, use o valor <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> em seu <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="29df9-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> <span data-ttu-id="29df9-142">O uso de <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requer o .NET Framework 4.7 (ou versões posteriores) ou o .NET Core 1.1 (ou versões posteriores).</span><span class="sxs-lookup"><span data-stu-id="29df9-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="29df9-143">Não está disponível no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="29df9-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="29df9-144">Se você estiver trabalhando com APIs COM, talvez seja necessário realizar marshal de uma cadeia de caracteres como um `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="29df9-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="29df9-145">Usando o valor <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, você pode realizar marshal de uma cadeia de caracteres como um `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="29df9-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

<span data-ttu-id="29df9-146">Ao usar uma API baseada no WinRT, talvez seja necessário realizar marshal de uma cadeia de caracteres como um `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="29df9-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="29df9-147">Usando o valor <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, você pode realizar marshal de uma cadeia de caracteres como um `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="29df9-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

<span data-ttu-id="29df9-148">Se sua API requer que você passe a cadeia de caracteres in-loco na estrutura, use o valor <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="29df9-149">A codificação de uma cadeia de caracteres com marshaling realizado por `ByValTStr` é determinada por meio do atributo `CharSet`.</span><span class="sxs-lookup"><span data-stu-id="29df9-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="29df9-150">Além disso, ela requer que o comprimento da cadeia de caracteres seja passado pelo campo <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="29df9-151">Personalização do marshaling de campo decimal</span><span class="sxs-lookup"><span data-stu-id="29df9-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="29df9-152">Se você estiver trabalhando no Windows, poderá encontrar algumas APIs que usam a estrutura [`CY` ou `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) nativa.</span><span class="sxs-lookup"><span data-stu-id="29df9-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="29df9-153">Por padrão, o tipo .NET `decimal` realizar marshal da estrutura nativa [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1).</span><span class="sxs-lookup"><span data-stu-id="29df9-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="29df9-154">No entanto, você pode usar um <xref:System.Runtime.InteropServices.MarshalAsAttribute> com o valor <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> para instruir o marshaler para converter um valor `decimal` para um valor nativo `CY`.</span><span class="sxs-lookup"><span data-stu-id="29df9-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a><span data-ttu-id="29df9-155">`System.Object`s de marshaling</span><span class="sxs-lookup"><span data-stu-id="29df9-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="29df9-156">No Windows, você pode realizar marshal dos campos tipados de `object` para o código nativo.</span><span class="sxs-lookup"><span data-stu-id="29df9-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="29df9-157">Você pode realizar marshal desses campos para um dos três tipos:</span><span class="sxs-lookup"><span data-stu-id="29df9-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="29df9-158">Por padrão, um campo tipado de `object` terá o marshaling realizado para um `IUnknown*` que encapsula o objeto.</span><span class="sxs-lookup"><span data-stu-id="29df9-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

<span data-ttu-id="29df9-159">Se você quiser realizar marshal de um campo de objeto para um `IDispatch*`, adicione um <xref:System.Runtime.InteropServices.MarshalAsAttribute> com o valor <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

<span data-ttu-id="29df9-160">Se você quiser realizar marshal dele como um `VARIANT`, adicione um <xref:System.Runtime.InteropServices.MarshalAsAttribute> com o valor <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29df9-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

<span data-ttu-id="29df9-161">A tabela a seguir descreve como diferentes tipos de tempo de execução do campo `obj` são mapeados para os vários tipos armazenados em um `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="29df9-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="29df9-162">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="29df9-162">.NET Type</span></span> | <span data-ttu-id="29df9-163">Tipo de VARIANTE</span><span class="sxs-lookup"><span data-stu-id="29df9-163">VARIANT Type</span></span> | | <span data-ttu-id="29df9-164">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="29df9-164">.NET Type</span></span> | <span data-ttu-id="29df9-165">Tipo de VARIANTE</span><span class="sxs-lookup"><span data-stu-id="29df9-165">VARIANT Type</span></span> |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
