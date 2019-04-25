---
title: Especificando um conjunto de caracteres
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 798fcacab5bd74dbd6569a68a3b598c0bb63a0a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087724"
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="6f3b0-102">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f3b0-102">Specifying a Character Set</span></span>
<span data-ttu-id="6f3b0-103">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> controla o marshaling de cadeia de caracteres e determina como a invocação de plataforma localiza os nomes de função em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="6f3b0-104">Este tópico descreve os dois comportamentos.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="6f3b0-105">Algumas APIs exportam duas versões de funções que usam argumentos de cadeia de caracteres: estreita (ANSI) e larga (Unicode).</span><span class="sxs-lookup"><span data-stu-id="6f3b0-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="6f3b0-106">A API do Windows, por exemplo, inclui os seguintes nomes do ponto de entrada para a função **MessageBox**:</span><span class="sxs-lookup"><span data-stu-id="6f3b0-106">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="6f3b0-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="6f3b0-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="6f3b0-108">Fornece a formatação ANSI de caracteres de 1 byte, diferenciada por um “A” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="6f3b0-109">Chamadas para **MessageBoxA** sempre realizam marshaling das cadeias de caracteres no formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-109">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
-   <span data-ttu-id="6f3b0-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="6f3b0-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="6f3b0-111">Fornece a formatação Unicode de caracteres de 2 bytes, diferenciada por um “W” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="6f3b0-112">Chamadas para **MessageBoxW** sempre realizam marshaling das cadeias de caracteres no formato Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-112">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="6f3b0-113">Marshaling de cadeia de caracteres e correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="6f3b0-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="6f3b0-114">O campo `CharSet` aceita os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6f3b0-114">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="6f3b0-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (valor padrão)</span><span class="sxs-lookup"><span data-stu-id="6f3b0-115"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
-   <span data-ttu-id="6f3b0-116">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f3b0-116">String marshaling</span></span>  
  
     <span data-ttu-id="6f3b0-117">A invocação de plataforma realiza marshaling das cadeias de caracteres de seu formato gerenciado (Unicode) para o formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="6f3b0-118">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="6f3b0-118">Name matching</span></span>  
  
     <span data-ttu-id="6f3b0-119">Quando o campo <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> é `true`, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="6f3b0-120">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará quando não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="6f3b0-121">Quando o campo `ExactSpelling` é `false`, que é o padrão no C++ e no C#, a invocação de plataforma procura o alias não danificado primeiro (**MessageBox**) e, em seguida, o nome danificado (**MessageBoxA**), se o alias não danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-121">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="6f3b0-122">Observe que o comportamento de correspondência de nomes do ANSI é diferente do comportamento de correspondência de nomes do Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
-   <span data-ttu-id="6f3b0-123">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f3b0-123">String marshaling</span></span>  
  
     <span data-ttu-id="6f3b0-124">A invocação de plataforma copia as cadeias de caracteres de seu formato gerenciado (Unicode) para o formato Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-124">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="6f3b0-125">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="6f3b0-125">Name matching</span></span>  
  
     <span data-ttu-id="6f3b0-126">Quando o campo `ExactSpelling` é `true`, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-126">When the `ExactSpelling` field is `true`, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="6f3b0-127">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará se não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-127">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="6f3b0-128">Quando o campo `ExactSpelling` é `false`, que é o padrão no C++ e no C#, a invocação de plataforma procura o nome danificado primeiro (**MessageBoxW**) e, em seguida, o alias não danificado (**MessageBox**), se o nome danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-128">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="6f3b0-129">Observe que o comportamento de correspondência de nomes do Unicode é diferente do comportamento de correspondência de nomes do ANSI.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-129">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
-   <span data-ttu-id="6f3b0-130">A invocação de plataforma escolhe entre os formatos ANSI e Unicode em tempo de execução, com base na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-130">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="6f3b0-131">Especificando um conjunto de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f3b0-131">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="6f3b0-132">O exemplo a seguir declara a função **MessageBox** três vezes, cada vez com um comportamento diferente do conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-132">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="6f3b0-133">É possível especificar o comportamento do conjunto de caracteres no Visual Basic adicionando a palavra-chave **Ansi**, **Unicode** ou **Auto** à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-133">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="6f3b0-134">Se você omitir a palavra-chave do conjunto de caracteres, como é feito na primeira instrução de declaração, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> usará como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-134">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="6f3b0-135">A segunda e a terceira instruções no exemplo especificam explicitamente um conjunto de caracteres com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-135">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="6f3b0-136">Especificando um conjunto de caracteres no C# e no C++</span><span class="sxs-lookup"><span data-stu-id="6f3b0-136">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="6f3b0-137">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifica o conjunto de caracteres subjacente como ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-137">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="6f3b0-138">O conjunto de caracteres controla como deve ser realizado o marshaling dos argumentos de cadeia de caracteres para um método.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-138">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="6f3b0-139">Use um dos seguintes formatos para indicar o conjunto de caracteres:</span><span class="sxs-lookup"><span data-stu-id="6f3b0-139">Use one of the following forms to indicate the character set:</span></span>  
  
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
  
 <span data-ttu-id="6f3b0-140">O exemplo a seguir mostra três definições gerenciadas da função **MessageBox** atribuída para especificar um conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-140">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="6f3b0-141">Na primeira definição, por sua omissão, o campo `CharSet` usa como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="6f3b0-141">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
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
  
## <a name="see-also"></a><span data-ttu-id="6f3b0-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f3b0-142">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="6f3b0-143">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="6f3b0-143">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="6f3b0-144">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="6f3b0-144">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="6f3b0-145">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="6f3b0-145">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
