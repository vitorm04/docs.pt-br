---
title: Especificando um conjunto de caracteres
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
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb2ae519b4a3d52c590f050ba728286898373ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-a-character-set"></a><span data-ttu-id="bf330-102">Especificando um conjunto de caracteres</span><span class="sxs-lookup"><span data-stu-id="bf330-102">Specifying a Character Set</span></span>
<span data-ttu-id="bf330-103">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> controla o marshaling de cadeia de caracteres e determina como a invocação de plataforma localiza os nomes de função em uma DLL.</span><span class="sxs-lookup"><span data-stu-id="bf330-103">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="bf330-104">Este tópico descreve os dois comportamentos.</span><span class="sxs-lookup"><span data-stu-id="bf330-104">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="bf330-105">Algumas APIs exportam duas versões de funções que usam argumentos de cadeia de caracteres: estreita (ANSI) e larga (Unicode).</span><span class="sxs-lookup"><span data-stu-id="bf330-105">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="bf330-106">A API do Win32, por exemplo, inclui os seguintes nomes do ponto de entrada para a função **MessageBox**:</span><span class="sxs-lookup"><span data-stu-id="bf330-106">The Win32 API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
-   <span data-ttu-id="bf330-107">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="bf330-107">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="bf330-108">Fornece a formatação ANSI de caracteres de 1 byte, diferenciada por um “A” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="bf330-108">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="bf330-109">As chamadas a **MessageBoxA** sempre realizam marshaling das cadeias de caracteres no formato ANSI, comportamento comum nas plataformas Windows 95 e Windows 98.</span><span class="sxs-lookup"><span data-stu-id="bf330-109">Calls to **MessageBoxA** always marshal strings in ANSI format, as is common on Windows 95 and Windows 98 platforms.</span></span>  
  
-   <span data-ttu-id="bf330-110">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="bf330-110">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="bf330-111">Fornece a formatação Unicode de caracteres de 2 bytes, diferenciada por um “W” acrescentado ao nome do ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="bf330-111">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="bf330-112">As chamadas a **MessageBoxW** sempre realizam marshaling das cadeias de caracteres no formato Unicode, comportamento comum nas plataformas Windows NT, Windows 2000 e Windows XP.</span><span class="sxs-lookup"><span data-stu-id="bf330-112">Calls to **MessageBoxW** always marshal strings in Unicode format, as is common on Windows NT, Windows 2000, and Windows XP platforms.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="bf330-113">Marshaling de cadeia de caracteres e correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="bf330-113">String Marshaling and Name Matching</span></span>  
 <span data-ttu-id="bf330-114">O campo **CharSet** aceita os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bf330-114">The **CharSet** field accepts the following values:</span></span>  
  
 <span data-ttu-id="bf330-115">**CharSet.Ansi** (valor padrão)</span><span class="sxs-lookup"><span data-stu-id="bf330-115">**CharSet.Ansi** (default value)</span></span>  
  
-   <span data-ttu-id="bf330-116">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bf330-116">String marshaling</span></span>  
  
     <span data-ttu-id="bf330-117">A invocação de plataforma realiza marshaling das cadeias de caracteres de seu formato gerenciado (Unicode) para o formato ANSI.</span><span class="sxs-lookup"><span data-stu-id="bf330-117">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
-   <span data-ttu-id="bf330-118">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="bf330-118">Name matching</span></span>  
  
     <span data-ttu-id="bf330-119">Quando o campo <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> é **true**, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="bf330-119">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="bf330-120">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará quando não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="bf330-120">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="bf330-121">Quando o campo **ExactSpelling** é **false**, que é o padrão no C++ e no C#, a invocação de plataforma procura o alias não danificado primeiro (**MessageBox**) e, em seguida, o nome danificado (**MessageBoxA**), se o alias não danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="bf330-121">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="bf330-122">Observe que o comportamento de correspondência de nomes do ANSI é diferente do comportamento de correspondência de nomes do Unicode.</span><span class="sxs-lookup"><span data-stu-id="bf330-122">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <span data-ttu-id="bf330-123">**CharSet.Unicode**</span><span class="sxs-lookup"><span data-stu-id="bf330-123">**CharSet.Unicode**</span></span>  
  
-   <span data-ttu-id="bf330-124">Marshaling de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bf330-124">String marshaling</span></span>  
  
     <span data-ttu-id="bf330-125">A invocação de plataforma copia as cadeias de caracteres de seu formato gerenciado (Unicode) para o formato Unicode.</span><span class="sxs-lookup"><span data-stu-id="bf330-125">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
-   <span data-ttu-id="bf330-126">Correspondência de nomes</span><span class="sxs-lookup"><span data-stu-id="bf330-126">Name matching</span></span>  
  
     <span data-ttu-id="bf330-127">Quando o campo **ExactSpelling** é **true**, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="bf330-127">When the **ExactSpelling** field is **true**, as it is by default in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="bf330-128">Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará se não conseguir localizar a ortografia exata.</span><span class="sxs-lookup"><span data-stu-id="bf330-128">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="bf330-129">Quando o campo **ExactSpelling** é **false**, que é o padrão no C++ e no C#, a invocação de plataforma procura o nome danificado primeiro (**MessageBoxW**) e, em seguida, o alias não danificado (**MessageBox**), se o nome danificado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="bf330-129">When the **ExactSpelling** field is **false**, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="bf330-130">Observe que o comportamento de correspondência de nomes do Unicode é diferente do comportamento de correspondência de nomes do ANSI.</span><span class="sxs-lookup"><span data-stu-id="bf330-130">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <span data-ttu-id="bf330-131">**CharSet.Auto**</span><span class="sxs-lookup"><span data-stu-id="bf330-131">**CharSet.Auto**</span></span>  
  
-   <span data-ttu-id="bf330-132">A invocação de plataforma escolhe entre os formatos ANSI e Unicode em tempo de execução, com base na plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="bf330-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specifying-a-character-set-in-visual-basic"></a><span data-ttu-id="bf330-133">Especificando um conjunto de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf330-133">Specifying a Character Set in Visual Basic</span></span>  
 <span data-ttu-id="bf330-134">O exemplo a seguir declara a função **MessageBox** três vezes, cada vez com um comportamento diferente do conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bf330-134">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="bf330-135">É possível especificar o comportamento do conjunto de caracteres no Visual Basic adicionando a palavra-chave **Ansi**, **Unicode** ou **Auto** à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="bf330-135">You can specify character-set behavior in Visual Basic by adding the **Ansi**, **Unicode**, or **Auto** keyword to the declaration statement.</span></span>  
  
 <span data-ttu-id="bf330-136">Se você omitir a palavra-chave do conjunto de caracteres, como é feito na primeira instrução de declaração, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> usará como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="bf330-136">If you omit the character-set keyword, as is done in the first declaration statement, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span> <span data-ttu-id="bf330-137">A segunda e a terceira instruções no exemplo especificam explicitamente um conjunto de caracteres com uma palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="bf330-137">The second and third statements in the example explicitly specify a character set with a keyword.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a><span data-ttu-id="bf330-138">Especificando um conjunto de caracteres no C# e no C++</span><span class="sxs-lookup"><span data-stu-id="bf330-138">Specifying a Character Set in C# and C++</span></span>  
 <span data-ttu-id="bf330-139">O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifica o conjunto de caracteres subjacente como ANSI ou Unicode.</span><span class="sxs-lookup"><span data-stu-id="bf330-139">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="bf330-140">O conjunto de caracteres controla como deve ser realizado o marshaling dos argumentos de cadeia de caracteres para um método.</span><span class="sxs-lookup"><span data-stu-id="bf330-140">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="bf330-141">Use um dos seguintes formatos para indicar o conjunto de caracteres:</span><span class="sxs-lookup"><span data-stu-id="bf330-141">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 <span data-ttu-id="bf330-142">O exemplo a seguir mostra três definições gerenciadas da função **MessageBox** atribuída para especificar um conjunto de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bf330-142">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="bf330-143">Na primeira definição, por sua omissão, o campo **CharSet** usa como padrão o conjunto de caracteres ANSI.</span><span class="sxs-lookup"><span data-stu-id="bf330-143">In the first definition, by its omission, the **CharSet** field defaults to the ANSI character set.</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf330-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf330-144">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="bf330-145">Criando protótipos em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="bf330-145">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="bf330-146">Exemplos de invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="bf330-146">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="bf330-147">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="bf330-147">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
