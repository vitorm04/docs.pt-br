---
title: Marshalling dos tipos – .NET
description: Saiba como o .NET realizar marshal de seus tipos para uma representação nativa.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2c62581d34e77f208b7764f955dfa37613615ee4
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411350"
---
# <a name="type-marshalling"></a><span data-ttu-id="8a873-103">Marshalling dos tipos</span><span class="sxs-lookup"><span data-stu-id="8a873-103">Type marshalling</span></span>

<span data-ttu-id="8a873-104">**Marshalling** é o processo de transformar tipos quando precisam atravessar entre código nativo e gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a873-104">**Marshalling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="8a873-105">O marshalling é necessário porque os tipos são diferentes, no código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a873-105">Marshalling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="8a873-106">No código gerenciado, por exemplo, você tem uma `String`; no mundo não gerenciado, as cadeias de caracteres podem ser Unicode ("larga"), não Unicode, terminada em nulo, ASCII, etc. Por padrão, o subsistema do P/Invoke tenta fazer a coisa certa com base no comportamento padrão, descrito neste artigo.</span><span class="sxs-lookup"><span data-stu-id="8a873-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="8a873-107">Contudo, nas situações em que você precisa de controle extra, pode utilizar o atributo [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) para especificar qual é o tipo esperado no lado não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a873-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="8a873-108">Por exemplo, se você quiser que a cadeia de caracteres seja enviada como uma cadeia de caracteres ANSI terminada em nulo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8a873-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshalling-common-types"></a><span data-ttu-id="8a873-109">Regras padrão para tipos comuns de marshalling</span><span class="sxs-lookup"><span data-stu-id="8a873-109">Default rules for marshalling common types</span></span>

<span data-ttu-id="8a873-110">Geralmente, o tempo de execução tenta fazer a "coisa certa" ao realizar marshal para exigir a menor quantidade de trabalho de você.</span><span class="sxs-lookup"><span data-stu-id="8a873-110">Generally, the runtime tries to do the "right thing" when marshalling to require the least amount of work from you.</span></span> <span data-ttu-id="8a873-111">As tabelas a seguir descrevem como cada tipo tem o marshal realizado padrão quando usado em um parâmetro ou campo.</span><span class="sxs-lookup"><span data-stu-id="8a873-111">The following tables describe how each type is marshalled by default when used in a parameter or field.</span></span> <span data-ttu-id="8a873-112">Os tipos de caracteres e números inteiros de largura fixa C99/C++11 são usados ​​para garantir que a tabela a seguir esteja correta para todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="8a873-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="8a873-113">Use qualquer tipo nativo que tenha os mesmos requisitos de alinhamento e tamanho que esses tipos.</span><span class="sxs-lookup"><span data-stu-id="8a873-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="8a873-114">Esta primeira tabela descreve os mapeamentos para vários tipos para os quais o marshalling é o mesmo para ambos P/Invoke e o marshalling do campo.</span><span class="sxs-lookup"><span data-stu-id="8a873-114">This first table describes the mappings for various types for whom the marshalling is the same for both P/Invoke and field marshalling.</span></span>

| <span data-ttu-id="8a873-115">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-115">.NET Type</span></span> | <span data-ttu-id="8a873-116">Tipo nativo</span><span class="sxs-lookup"><span data-stu-id="8a873-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="8a873-117">`char` ou `char16_t` dependendo do `CharSet` do P/Invoke ou da estrutura.</span><span class="sxs-lookup"><span data-stu-id="8a873-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="8a873-118">Confira a [documentação do conjunto de caracteres](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="8a873-118">See the [charset documentation](/.charset.md).</span></span> |
| `string`  | <span data-ttu-id="8a873-119">`char*` ou `char16_t*` dependendo do `CharSet` do P/Invoke ou da estrutura.</span><span class="sxs-lookup"><span data-stu-id="8a873-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="8a873-120">Confira a [documentação do conjunto de caracteres](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="8a873-120">See the [charset documentation](/.charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="8a873-121">Tipos de ponteiro do .NET (por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8a873-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="8a873-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="8a873-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="8a873-123">Tipo derivado de `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="8a873-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="8a873-124">Tipo derivado de `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="8a873-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="8a873-125">Tipo `BOOL` Win32</span><span class="sxs-lookup"><span data-stu-id="8a873-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="8a873-126">Struct `DECIMAL` COM</span><span class="sxs-lookup"><span data-stu-id="8a873-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="8a873-127">Representante do .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-127">.NET Delegate</span></span> | <span data-ttu-id="8a873-128">Ponteiro de função nativo</span><span class="sxs-lookup"><span data-stu-id="8a873-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="8a873-129">Tipo `DATE` Win32</span><span class="sxs-lookup"><span data-stu-id="8a873-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="8a873-130">Tipo `GUID` Win32</span><span class="sxs-lookup"><span data-stu-id="8a873-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="8a873-131">Algumas categorias de marshalling têm padrões diferentes se você estiver realizando marshaling como um parâmetro ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8a873-131">A few categories of marshalling have different defaults if you're marshalling as a parameter or structure.</span></span>

| <span data-ttu-id="8a873-132">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-132">.NET Type</span></span> | <span data-ttu-id="8a873-133">Tipo nativo (parâmetro)</span><span class="sxs-lookup"><span data-stu-id="8a873-133">Native Type (Parameter)</span></span> | <span data-ttu-id="8a873-134">Tipo nativo (campo)</span><span class="sxs-lookup"><span data-stu-id="8a873-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="8a873-135">Matriz .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-135">.NET array</span></span> | <span data-ttu-id="8a873-136">Um ponteiro para o início de uma matriz de representações nativas dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="8a873-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="8a873-137">Não é permitido sem um atributo `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="8a873-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="8a873-138">Uma classe com um `LayoutKind` de `Sequential` ou `Explicit`</span><span class="sxs-lookup"><span data-stu-id="8a873-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="8a873-139">Um ponteiro para a representação nativa da classe</span><span class="sxs-lookup"><span data-stu-id="8a873-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="8a873-140">A representação nativa da classe</span><span class="sxs-lookup"><span data-stu-id="8a873-140">The native representation of the class</span></span> |

<span data-ttu-id="8a873-141">A tabela a seguir inclui as regras de marshalling padrão que são somente do Windows.</span><span class="sxs-lookup"><span data-stu-id="8a873-141">The following table includes the default marshalling rules that are Windows-only.</span></span> <span data-ttu-id="8a873-142">Em plataformas que não são Windows, você não pode realizar marshal desses tipos.</span><span class="sxs-lookup"><span data-stu-id="8a873-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="8a873-143">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-143">.NET Type</span></span> | <span data-ttu-id="8a873-144">Tipo nativo (parâmetro)</span><span class="sxs-lookup"><span data-stu-id="8a873-144">Native Type (Parameter)</span></span> | <span data-ttu-id="8a873-145">Tipo nativo (campo)</span><span class="sxs-lookup"><span data-stu-id="8a873-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="8a873-146">Interface COM</span><span class="sxs-lookup"><span data-stu-id="8a873-146">COM interface</span></span> | <span data-ttu-id="8a873-147">Não é permitida sem um atributo `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="8a873-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="8a873-148">Não permitida</span><span class="sxs-lookup"><span data-stu-id="8a873-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="8a873-149">Não permitida</span><span class="sxs-lookup"><span data-stu-id="8a873-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="8a873-150">Não permitida</span><span class="sxs-lookup"><span data-stu-id="8a873-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="8a873-151">`int64_t` representando o número de tiques desde a meia-noite de 1º de janeiro de 1601</span><span class="sxs-lookup"><span data-stu-id="8a873-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="8a873-152">`int64_t` representando o número de tiques desde a meia-noite de 1º de janeiro de 1601</span><span class="sxs-lookup"><span data-stu-id="8a873-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="8a873-153">Alguns tipos só podem ter o marshal realizado como parâmetros e não como campos.</span><span class="sxs-lookup"><span data-stu-id="8a873-153">Some types can only be marshalled as parameters and not as fields.</span></span> <span data-ttu-id="8a873-154">Esses tipos estão listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="8a873-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="8a873-155">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8a873-155">.NET Type</span></span> | <span data-ttu-id="8a873-156">Tipo nativo (parâmetro somente)</span><span class="sxs-lookup"><span data-stu-id="8a873-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="8a873-157">`char*` ou `char16_t*` dependendo do `CharSet` do P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="8a873-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="8a873-158">Confira a [documentação do conjunto de caracteres](/.charset.md).</span><span class="sxs-lookup"><span data-stu-id="8a873-158">See the [charset documentation](/.charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="8a873-159">`va_list` (no Windows x86/x64/arm64 somente)</span><span class="sxs-lookup"><span data-stu-id="8a873-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="8a873-160">Se esses padrões não fizerem exatamente o que você deseja, personalize como os parâmetros têm o marshal realizado.</span><span class="sxs-lookup"><span data-stu-id="8a873-160">If these defaults don't do exactly what you want, you can customize how parameters are marshalled.</span></span> <span data-ttu-id="8a873-161">O artigo sobre [ marshalling do parâmetro](customize-parameter-marshalling.md) explica como personalizar a forma como os tipos de parâmetros diferentes têm o marshal realizado.</span><span class="sxs-lookup"><span data-stu-id="8a873-161">The [parameter marshalling](customize-parameter-marshalling.md) article walks you through how to customize how different parameter types are marshalled.</span></span>

## <a name="marshalling-classes-and-structs"></a><span data-ttu-id="8a873-162">Marshalling de classes e structs</span><span class="sxs-lookup"><span data-stu-id="8a873-162">Marshalling classes and structs</span></span>

<span data-ttu-id="8a873-163">Outro aspecto do marshalling de tipos é como passar um struct para um método não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a873-163">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="8a873-164">Por exemplo, alguns dos métodos não gerenciados requerem um struct como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a873-164">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="8a873-165">Nesses casos, você precisa criar um struct correspondente ou uma classe na parte gerenciada do mundo para usar como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8a873-165">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="8a873-166">No entanto, definir a classe não é suficiente; também é necessário ensinar o marshaler como mapear campos na classe para o struct não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a873-166">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="8a873-167">Aqui, o atributo `StructLayout` se torna útil.</span><span class="sxs-lookup"><span data-stu-id="8a873-167">Here the `StructLayout` attribute becomes useful.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="8a873-168">O código anterior mostra um exemplo simples de chamar para a função `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="8a873-168">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="8a873-169">A parte interessante está na linha 4.</span><span class="sxs-lookup"><span data-stu-id="8a873-169">The interesting bit is on line 4.</span></span> <span data-ttu-id="8a873-170">O atributo especifica que os campos da classe devem ser mapeados em sequência até o struct no outro lado (não gerenciado).</span><span class="sxs-lookup"><span data-stu-id="8a873-170">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="8a873-171">Isso significa que os nomes dos campos não são importantes, apenas sua ordem é importante, já que precisa corresponder ao struct não gerenciado, mostrado no exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="8a873-171">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="8a873-172">Às vezes, o marshalling padrão para sua estrutura não faz o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="8a873-172">Sometimes the default marshalling for your structure doesn't do what you need.</span></span> <span data-ttu-id="8a873-173">O artigo [Personalizando o marshalling de estrutura](./customize-struct-marshalling.md) ensina como personalizar a forma como sua estrutura tem o marshal realizado.</span><span class="sxs-lookup"><span data-stu-id="8a873-173">The [Customizing structure marshalling](./customize-struct-marshalling.md) article teaches you how to customize how your structure is marshaled.</span></span>
