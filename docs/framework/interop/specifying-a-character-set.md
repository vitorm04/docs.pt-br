---
title: Especificando um conjunto de caracteres
description: Saiba como especificar um conjunto de caracteres que usa codificação estreita (ANSI) ou larga (Unicode). Alternativamente, você pode especificar a seleção automática de tempo de execução.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 789753742d8714e481f038e323407cbab0499f6c
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309788"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="99318-104">Especificar um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="99318-104">Specify a character set</span></span>

<span data-ttu-id="99318-105">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> controla o marshaling de cadeia de caracteres e determina como a invocação de plataforma localiza os nomes de função em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="99318-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="99318-106">Este tópico descreve os dois comportamentos.</span><span class="sxs-lookup"><span data-stu-id="99318-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="99318-107">Algumas APIs exportam duas versões de funções que usam argumentos de cadeia de caracteres: estreita (ANSI) e larga (Unicode).</span><span class="sxs-lookup"><span data-stu-id="99318-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="99318-108">A API do Windows, por exemplo, inclui os seguintes nomes do ponto de entrada para a função **MessageBox**:</span><span class="sxs-lookup"><span data-stu-id="99318-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="99318-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="99318-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="99318-110">Fornece a formatação ANSI de caracteres de 1 byte, diferenciada por um “A” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="99318-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="99318-111">Chamadas para **MessageBoxA** sempre realizam marshaling das cadeias de caracteres no formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="99318-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="99318-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="99318-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="99318-113">Fornece a formatação Unicode de caracteres de 2 bytes, diferenciada por um “W” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="99318-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="99318-114">Chamadas para **MessageBoxW** sempre realizam marshaling das cadeias de caracteres no formato Unicode.</span><span class="sxs-lookup"><span data-stu-id="99318-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="99318-115">Marshaling de cadeia de caracteres e correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="99318-115">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="99318-116">O campo `CharSet` aceita os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="99318-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="99318-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (valor padrão)</span><span class="sxs-lookup"><span data-stu-id="99318-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="99318-118">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="99318-118">String marshaling</span></span>  
  
     <span data-ttu-id="99318-119">A invocação de plataforma realiza marshaling das cadeias de caracteres de seu formato gerenciado (Unicode) para o formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="99318-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="99318-120">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="99318-120">Name matching</span></span>  
  
     <span data-ttu-id="99318-121">Quando o campo <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> é `true`, como é o padrão no Visual Basic, a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="99318-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="99318-122">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará quando não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="99318-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="99318-123">Quando o campo `ExactSpelling` é `false`, que é o padrão no C++ e no C#, a invocação de plataforma procura o alias não danificado primeiro (**MessageBox**) e, em seguida, o nome danificado (**MessageBoxA**), se o alias não danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="99318-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="99318-124">Observe que o comportamento de correspondência de nomes do ANSI é diferente do comportamento de correspondência de nomes do Unicode.</span><span class="sxs-lookup"><span data-stu-id="99318-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="99318-125">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="99318-125">String marshaling</span></span>  
  
     <span data-ttu-id="99318-126">A invocação de plataforma copia as cadeias de caracteres de seu formato gerenciado (Unicode) para o formato Unicode.</span><span class="sxs-lookup"><span data-stu-id="99318-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="99318-127">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="99318-127">Name matching</span></span>  
  
     <span data-ttu-id="99318-128">Quando o campo `ExactSpelling` é `true`, como é o padrão no Visual Basic, a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="99318-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="99318-129">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará se não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="99318-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="99318-130">Quando o campo `ExactSpelling` é `false`, que é o padrão no C++ e no C#, a invocação de plataforma procura o nome danificado primeiro (**MessageBoxW**) e, em seguida, o alias não danificado (**MessageBox**), se o nome danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="99318-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="99318-131">Observe que o comportamento de correspondência de nomes do Unicode é diferente do comportamento de correspondência de nomes do ANSI.</span><span class="sxs-lookup"><span data-stu-id="99318-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="99318-132">A invocação de plataforma escolhe entre os formatos ANSI e Unicode em tempo de execução, com base na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="99318-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="99318-133">Especifique um conjunto de caracteres em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99318-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="99318-134">Você pode especificar o comportamento do conjunto de caracteres no Visual Basic adicionando `Ansi` a `Unicode` `Auto` palavra-chave, ou à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="99318-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="99318-135">Se você omitir a palavra-chave de conjunto de caracteres, o <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> campo usa como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="99318-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="99318-136">O exemplo a seguir declara a função **MessageBox** três vezes, cada vez com um comportamento diferente do conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="99318-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="99318-137">A primeira instrução omite a palavra-chave de conjunto de caracteres, de modo que o conjunto de caracteres usa ANSI como padrão.</span><span class="sxs-lookup"><span data-stu-id="99318-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="99318-138">A segunda e terceira instruções especificam explicitamente um conjunto de caracteres com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="99318-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="99318-139">Especificar um conjunto de caracteres em C# e C++</span><span class="sxs-lookup"><span data-stu-id="99318-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="99318-140">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifica o conjunto de caracteres subjacente como ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="99318-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="99318-141">O conjunto de caracteres controla como deve ser realizado o marshaling dos argumentos de cadeia de caracteres para um método.</span><span class="sxs-lookup"><span data-stu-id="99318-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="99318-142">Use um dos seguintes formatos para indicar o conjunto de caracteres:</span><span class="sxs-lookup"><span data-stu-id="99318-142">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="99318-143">O exemplo a seguir mostra três definições gerenciadas da função **MessageBox** atribuída para especificar um conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="99318-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="99318-144">Na primeira definição, por sua omissão, o campo `CharSet` usa como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="99318-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="99318-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="99318-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="99318-146">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="99318-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="99318-147">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="99318-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="99318-148">Marshaling de dados com invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="99318-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
