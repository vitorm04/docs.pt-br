---
title: Marshaling de tipo – .NET
description: Saiba como o .NET realizar marshal de seus tipos para uma representação nativa.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2cb8898b52b4b4afba1184a886e16c9f7f68f03a
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041792"
---
# <a name="type-marshaling"></a><span data-ttu-id="83da4-103">Marshaling de tipo</span><span class="sxs-lookup"><span data-stu-id="83da4-103">Type marshaling</span></span>

<span data-ttu-id="83da4-104">**Marshaling** é o processo de transformar tipos quando precisam atravessar entre código nativo e gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83da4-104">**Marshaling** is the process of transforming types when they need to cross between managed and native code.</span></span>

<span data-ttu-id="83da4-105">O marshaling é necessário porque os tipos são diferentes, no código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83da4-105">Marshaling is needed because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="83da4-106">No código gerenciado, por exemplo, você tem uma `String`; no mundo não gerenciado, as cadeias de caracteres podem ser Unicode ("larga"), não Unicode, terminada em nulo, ASCII, etc. Por padrão, o subsistema do P/Invoke tenta fazer a coisa certa com base no comportamento padrão, descrito neste artigo.</span><span class="sxs-lookup"><span data-stu-id="83da4-106">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem tries to do the right thing based on the default behavior, described on this article.</span></span> <span data-ttu-id="83da4-107">Contudo, nas situações em que você precisa de controle extra, pode utilizar o atributo [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) para especificar qual é o tipo esperado no lado não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83da4-107">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="83da4-108">Por exemplo, se você quiser que a cadeia de caracteres seja enviada como uma cadeia de caracteres ANSI terminada em nulo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="83da4-108">For instance, if you want the string to be sent as a null-terminated ANSI string, you could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a><span data-ttu-id="83da4-109">Regras padrão para tipos comuns de marshaling</span><span class="sxs-lookup"><span data-stu-id="83da4-109">Default rules for marshaling common types</span></span>

<span data-ttu-id="83da4-110">Geralmente, o tempo de execução tenta fazer a "coisa certa" ao realizar marshaling para exigir a menor quantidade de trabalho de você.</span><span class="sxs-lookup"><span data-stu-id="83da4-110">Generally, the runtime tries to do the "right thing" when marshaling to require the least amount of work from you.</span></span> <span data-ttu-id="83da4-111">As tabelas a seguir descrevem como cada tipo tem o marshaling realizado por padrão quando usado em um parâmetro ou campo.</span><span class="sxs-lookup"><span data-stu-id="83da4-111">The following tables describe how each type is marshaled by default when used in a parameter or field.</span></span> <span data-ttu-id="83da4-112">Os tipos de caracteres e números inteiros de largura fixa C99/C++11 são usados ​​para garantir que a tabela a seguir esteja correta para todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="83da4-112">The C99/C++11 fixed-width integer and character types are used to ensure that the following table is correct for all platforms.</span></span> <span data-ttu-id="83da4-113">Use qualquer tipo nativo que tenha os mesmos requisitos de alinhamento e tamanho que esses tipos.</span><span class="sxs-lookup"><span data-stu-id="83da4-113">You can use any native type that has the same alignment and size requirements as these types.</span></span>

<span data-ttu-id="83da4-114">Esta primeira tabela descreve os mapeamentos para vários tipos para os quais o marshaling é o mesmo para ambos P/Invoke e o marshaling do campo.</span><span class="sxs-lookup"><span data-stu-id="83da4-114">This first table describes the mappings for various types for whom the marshaling is the same for both P/Invoke and field marshaling.</span></span>

| <span data-ttu-id="83da4-115">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-115">.NET Type</span></span> | <span data-ttu-id="83da4-116">Tipo nativo</span><span class="sxs-lookup"><span data-stu-id="83da4-116">Native Type</span></span>  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | <span data-ttu-id="83da4-117">`char` ou `char16_t` dependendo do `CharSet` do P/Invoke ou da estrutura.</span><span class="sxs-lookup"><span data-stu-id="83da4-117">Either `char` or `char16_t` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="83da4-118">Confira a [documentação do conjunto de caracteres](charset.md).</span><span class="sxs-lookup"><span data-stu-id="83da4-118">See the [charset documentation](charset.md).</span></span> |
| `string`  | <span data-ttu-id="83da4-119">`char*` ou `char16_t*` dependendo do `CharSet` do P/Invoke ou da estrutura.</span><span class="sxs-lookup"><span data-stu-id="83da4-119">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke or structure.</span></span> <span data-ttu-id="83da4-120">Confira a [documentação do conjunto de caracteres](charset.md).</span><span class="sxs-lookup"><span data-stu-id="83da4-120">See the [charset documentation](charset.md).</span></span> |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| <span data-ttu-id="83da4-121">Tipos de ponteiro do .NET (por exemplo:</span><span class="sxs-lookup"><span data-stu-id="83da4-121">.NET Pointer types (ex.</span></span> <span data-ttu-id="83da4-122">`void*`)</span><span class="sxs-lookup"><span data-stu-id="83da4-122">`void*`)</span></span>  | `void*` |
| <span data-ttu-id="83da4-123">Tipo derivado de `System.Runtime.InteropServices.SafeHandle`</span><span class="sxs-lookup"><span data-stu-id="83da4-123">Type derived from `System.Runtime.InteropServices.SafeHandle`</span></span> | `void*` |
| <span data-ttu-id="83da4-124">Tipo derivado de `System.Runtime.InteropServices.CriticalHandle`</span><span class="sxs-lookup"><span data-stu-id="83da4-124">Type derived from `System.Runtime.InteropServices.CriticalHandle`</span></span> | `void*`          |
| `bool`    | <span data-ttu-id="83da4-125">Tipo `BOOL` Win32</span><span class="sxs-lookup"><span data-stu-id="83da4-125">Win32 `BOOL` type</span></span>       |
| `decimal` | <span data-ttu-id="83da4-126">Struct `DECIMAL` COM</span><span class="sxs-lookup"><span data-stu-id="83da4-126">COM `DECIMAL` struct</span></span> |
| <span data-ttu-id="83da4-127">Representante do .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-127">.NET Delegate</span></span> | <span data-ttu-id="83da4-128">Ponteiro de função nativo</span><span class="sxs-lookup"><span data-stu-id="83da4-128">Native function pointer</span></span> |
| `System.DateTime` | <span data-ttu-id="83da4-129">Tipo `DATE` Win32</span><span class="sxs-lookup"><span data-stu-id="83da4-129">Win32 `DATE` type</span></span> |
| `System.Guid` | <span data-ttu-id="83da4-130">Tipo `GUID` Win32</span><span class="sxs-lookup"><span data-stu-id="83da4-130">Win32 `GUID` type</span></span> |

<span data-ttu-id="83da4-131">Algumas categorias de marshaling terão padrões diferentes se você estiver realizando marshaling como um parâmetro ou uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="83da4-131">A few categories of marshaling have different defaults if you're marshaling as a parameter or structure.</span></span>

| <span data-ttu-id="83da4-132">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-132">.NET Type</span></span> | <span data-ttu-id="83da4-133">Tipo nativo (parâmetro)</span><span class="sxs-lookup"><span data-stu-id="83da4-133">Native Type (Parameter)</span></span> | <span data-ttu-id="83da4-134">Tipo nativo (campo)</span><span class="sxs-lookup"><span data-stu-id="83da4-134">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| <span data-ttu-id="83da4-135">Matriz .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-135">.NET array</span></span> | <span data-ttu-id="83da4-136">Um ponteiro para o início de uma matriz de representações nativas dos elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="83da4-136">A pointer to the start of an array of native representations of the array elements.</span></span> | <span data-ttu-id="83da4-137">Não é permitido sem um atributo `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="83da4-137">Not allowed without a `[MarshalAs]` attribute</span></span>|
| <span data-ttu-id="83da4-138">Uma classe com um `LayoutKind` de `Sequential` ou `Explicit`</span><span class="sxs-lookup"><span data-stu-id="83da4-138">A class with a `LayoutKind` of `Sequential` or `Explicit`</span></span> | <span data-ttu-id="83da4-139">Um ponteiro para a representação nativa da classe</span><span class="sxs-lookup"><span data-stu-id="83da4-139">A pointer to the native representation of the class</span></span> | <span data-ttu-id="83da4-140">A representação nativa da classe</span><span class="sxs-lookup"><span data-stu-id="83da4-140">The native representation of the class</span></span> |

<span data-ttu-id="83da4-141">A tabela a seguir inclui as regras de marshaling padrão que são somente do Windows.</span><span class="sxs-lookup"><span data-stu-id="83da4-141">The following table includes the default marshaling rules that are Windows-only.</span></span> <span data-ttu-id="83da4-142">Em plataformas que não são Windows, você não pode realizar marshal desses tipos.</span><span class="sxs-lookup"><span data-stu-id="83da4-142">On non-Windows platforms, you cannot marshal these types.</span></span>

| <span data-ttu-id="83da4-143">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-143">.NET Type</span></span> | <span data-ttu-id="83da4-144">Tipo nativo (parâmetro)</span><span class="sxs-lookup"><span data-stu-id="83da4-144">Native Type (Parameter)</span></span> | <span data-ttu-id="83da4-145">Tipo nativo (campo)</span><span class="sxs-lookup"><span data-stu-id="83da4-145">Native Type (Field)</span></span> |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | <span data-ttu-id="83da4-146">Interface COM</span><span class="sxs-lookup"><span data-stu-id="83da4-146">COM interface</span></span> | <span data-ttu-id="83da4-147">Não é permitida sem um atributo `[MarshalAs]`</span><span class="sxs-lookup"><span data-stu-id="83da4-147">Not allowed without a `[MarshalAs]` attribute</span></span> |
| `System.ArgIterator` | `va_list` | <span data-ttu-id="83da4-148">Não permitida</span><span class="sxs-lookup"><span data-stu-id="83da4-148">Not allowed</span></span> |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | <span data-ttu-id="83da4-149">Não permitida</span><span class="sxs-lookup"><span data-stu-id="83da4-149">Not allowed</span></span> |
| `System.Collections.IEnumerable` | `IDispatch*` | <span data-ttu-id="83da4-150">Não permitida</span><span class="sxs-lookup"><span data-stu-id="83da4-150">Not allowed</span></span> |
| `System.DateTimeOffset` | <span data-ttu-id="83da4-151">`int64_t` representando o número de tiques desde a meia-noite de 1º de janeiro de 1601</span><span class="sxs-lookup"><span data-stu-id="83da4-151">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> || <span data-ttu-id="83da4-152">`int64_t` representando o número de tiques desde a meia-noite de 1º de janeiro de 1601</span><span class="sxs-lookup"><span data-stu-id="83da4-152">`int64_t` representing the number of ticks since midnight on January 1, 1601</span></span> |

<span data-ttu-id="83da4-153">Alguns tipos só podem ter o marshaling realizado como parâmetros e não como campos.</span><span class="sxs-lookup"><span data-stu-id="83da4-153">Some types can only be marshaled as parameters and not as fields.</span></span> <span data-ttu-id="83da4-154">Esses tipos estão listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="83da4-154">These types are listed in the following table:</span></span>

| <span data-ttu-id="83da4-155">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-155">.NET Type</span></span> | <span data-ttu-id="83da4-156">Tipo nativo (parâmetro somente)</span><span class="sxs-lookup"><span data-stu-id="83da4-156">Native Type (Parameter Only)</span></span> |
|-----------|------------------------------|
| `System.Text.StringBuilder` | <span data-ttu-id="83da4-157">`char*` ou `char16_t*` dependendo do `CharSet` do P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="83da4-157">Either `char*` or `char16_t*` depending on the `CharSet` of the P/Invoke.</span></span>  <span data-ttu-id="83da4-158">Confira a [documentação do conjunto de caracteres](charset.md).</span><span class="sxs-lookup"><span data-stu-id="83da4-158">See the [charset documentation](charset.md).</span></span> |
| `System.ArgIterator` | <span data-ttu-id="83da4-159">`va_list` (no Windows x86/x64/arm64 somente)</span><span class="sxs-lookup"><span data-stu-id="83da4-159">`va_list` (on Windows x86/x64/arm64 only)</span></span> |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

<span data-ttu-id="83da4-160">Se esses padrões não fizerem exatamente o que você deseja, personalize como os parâmetros têm o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="83da4-160">If these defaults don't do exactly what you want, you can customize how parameters are marshaled.</span></span> <span data-ttu-id="83da4-161">O artigo sobre [marshaling de parâmetro](customize-parameter-marshaling.md) explica como personalizar a forma como os tipos de parâmetros diferentes têm o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="83da4-161">The [parameter marshaling](customize-parameter-marshaling.md) article walks you through how to customize how different parameter types are marshaled.</span></span>

## <a name="default-marshaling-in-com-scenarios"></a><span data-ttu-id="83da4-162">Marshaling padrão em cenários COM</span><span class="sxs-lookup"><span data-stu-id="83da4-162">Default marshaling in COM scenarios</span></span>

<span data-ttu-id="83da4-163">Quando você chama métodos em objetos COM no .NET, o tempo de execução do .NET altera a regras de marshaling padrão para corresponder à semântica de COM.</span><span class="sxs-lookup"><span data-stu-id="83da4-163">When you are calling methods on COM objects in .NET, the .NET runtime changes the default marshaling rules to match common COM semantics.</span></span> <span data-ttu-id="83da4-164">A tabela a seguir lista as regras que os tempos de execução do .NET usam em cenários COM:</span><span class="sxs-lookup"><span data-stu-id="83da4-164">The following table lists the rules that .NET runtimes uses in COM scenarios:</span></span>

| <span data-ttu-id="83da4-165">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-165">.NET Type</span></span> | <span data-ttu-id="83da4-166">Tipo nativo (chamadas de método COM)</span><span class="sxs-lookup"><span data-stu-id="83da4-166">Native Type (COM method calls)</span></span> |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| <span data-ttu-id="83da4-167">Tipos delegados</span><span class="sxs-lookup"><span data-stu-id="83da4-167">Delegate types</span></span> | <span data-ttu-id="83da4-168">`_Delegate*` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83da4-168">`_Delegate*` in .NET Framework.</span></span> <span data-ttu-id="83da4-169">Não permitido no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="83da4-169">Disallowed in .NET Core.</span></span> |
| `System.Drawing.Color` | `OLECOLOR`        |
| <span data-ttu-id="83da4-170">Matriz .NET</span><span class="sxs-lookup"><span data-stu-id="83da4-170">.NET array</span></span> | `SAFEARRAY`                   |
| `string[]` | <span data-ttu-id="83da4-171">`SAFEARRAY` de `BSTR`s</span><span class="sxs-lookup"><span data-stu-id="83da4-171">`SAFEARRAY` of `BSTR`s</span></span>        |

## <a name="marshaling-classes-and-structs"></a><span data-ttu-id="83da4-172">Marshaling de classes e structs</span><span class="sxs-lookup"><span data-stu-id="83da4-172">Marshaling classes and structs</span></span>

<span data-ttu-id="83da4-173">Outro aspecto do marshaling de tipos é como passar um struct para um método não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83da4-173">Another aspect of type marshaling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="83da4-174">Por exemplo, alguns dos métodos não gerenciados requerem um struct como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="83da4-174">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="83da4-175">Nesses casos, você precisa criar um struct correspondente ou uma classe na parte gerenciada do mundo para usar como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="83da4-175">In these cases, you need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="83da4-176">No entanto, definir a classe não é suficiente; também é necessário ensinar o marshaler como mapear campos na classe para o struct não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="83da4-176">However, just defining the class isn't enough, you also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="83da4-177">Aqui, o atributo `StructLayout` se torna útil.</span><span class="sxs-lookup"><span data-stu-id="83da4-177">Here the `StructLayout` attribute becomes useful.</span></span>

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

<span data-ttu-id="83da4-178">O código anterior mostra um exemplo simples de chamar para a função `GetSystemTime()`.</span><span class="sxs-lookup"><span data-stu-id="83da4-178">The previous code shows a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="83da4-179">A parte interessante está na linha 4.</span><span class="sxs-lookup"><span data-stu-id="83da4-179">The interesting bit is on line 4.</span></span> <span data-ttu-id="83da4-180">O atributo especifica que os campos da classe devem ser mapeados em sequência até o struct no outro lado (não gerenciado).</span><span class="sxs-lookup"><span data-stu-id="83da4-180">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="83da4-181">Isso significa que os nomes dos campos não são importantes, apenas sua ordem é importante, já que precisa corresponder ao struct não gerenciado, mostrado no exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="83da4-181">This means that the naming of the fields isn't important, only their order is important, as it needs to correspond to the unmanaged struct, shown in the following example:</span></span>

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

<span data-ttu-id="83da4-182">Às vezes, o marshaling padrão para sua estrutura não faz o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="83da4-182">Sometimes the default marshaling for your structure doesn't do what you need.</span></span> <span data-ttu-id="83da4-183">O artigo [Personalizando o marshaling de estrutura](./customize-struct-marshaling.md) ensina como personalizar a forma como sua estrutura tem o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="83da4-183">The [Customizing structure marshaling](./customize-struct-marshaling.md) article teaches you how to customize how your structure is marshaled.</span></span>
