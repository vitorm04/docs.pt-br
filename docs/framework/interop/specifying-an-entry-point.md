---
title: Especificando um ponto de entrada
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 787406b1fa7e5beb59ff3f8715c1215a734ed895
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411298"
---
# <a name="specifying-an-entry-point"></a>Especificando um ponto de entrada
Um ponto de entrada identifica o local de uma função em uma DLL. Em um projeto gerenciado, o nome original ou o ponto de entrada ordinal de uma função de destino identifica essa função no limite de interoperação. Além disso, é possível mapear o ponto de entrada para um nome diferente, renomeando a função efetivamente.  
  
 Veja a seguir uma lista dos possíveis motivos para renomear uma função de DLL:  
  
-   Para evitar o uso de nomes de função de API que diferenciam maiúsculas de minúsculas  
  
-   Para estar em conformidade com os padrões de nomenclatura existentes  
  
-   Para acomodar funções que usam tipos de dados diferentes (declarando várias versões da mesma função de DLL)  
  
-   Para simplificar o uso de APIs que contêm versões ANSI e Unicode  
  
 Este tópico demonstra como renomear uma função de DLL em um código gerenciado.  
  
## <a name="renaming-a-function-in-visual-basic"></a>Renomeando uma função no Visual Basic  
 O Visual Basic usa a palavra-chave **Function** na instrução **Declare** para definir o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType>. O exemplo a seguir mostra uma declaração básica.  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 É possível substituir o ponto de entrada **MessageBox** por **MsgBox** incluindo a palavra-chave **Alias** na definição, conforme mostrado no exemplo a seguir. Nos dois exemplos, a palavra-chave **Auto** elimina a necessidade de especificar a versão do conjunto de caracteres do ponto de entrada. Para obter mais informações sobre como selecionar um conjunto de caracteres, consulte [Especificando um conjunto de caracteres](../../../docs/framework/interop/specifying-a-character-set.md).  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a>Renomeando uma função no C# e C++  
 É possível usar o campo <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> para especificar uma função de DLL por nome ou ordinal. Se o nome da função na definição de método for o mesmo do ponto de entrada na DLL, você não precisará identificar explicitamente a função com o campo **EntryPoint**. Caso contrário, use um dos seguintes formatos de atributo para indicar um nome ou um ordinal:  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 Observe que é necessário prefixar um ordinal com o sinal de cerquilha (#).  
  
 O exemplo a seguir demonstra como substituir **MessageBoxA** por **MsgBox** no código usando o campo **EntryPoint**.  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [Exemplos de invocação de plataforma](../../../docs/framework/interop/platform-invoke-examples.md)
- [Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
