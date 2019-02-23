---
title: Assemblies amigáveis (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 9b91f894f9b10c85eb322b4421fd0473335df7a3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748148"
---
# <a name="friend-assemblies-visual-basic"></a>Assemblies amigáveis (Visual Basic)
Um *assembly amigável* é um assembly que pode acessar outro assembly [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) tipos e membros. Se você identificar um assembly como um assembly amigável, não precisará marcar os tipos e membros como públicos para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nos seguintes cenários:  
  
-   Durante o teste de unidade, quando o código de teste é executado um assembly separado, mas requer acesso a membros no assembly que está sendo testado que são marcados como `Friend`.  
  
-   Quando você estiver desenvolvendo uma biblioteca de classes e adições à biblioteca estão contidas em assemblies separados, mas exigem acesso a membros em assemblies existentes que são marcados como `Friend`.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> para identificar um ou mais assemblies amigáveis para um determinado assembly. O exemplo a seguir usa o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> no assembly A e especifica o assembly `AssemblyB` como um assembly amigável. Isso fornece ao assembly `AssemblyB` acesso a todos os tipos e membros no assembly A que são marcados como `Friend`.  
  
> [!NOTE]
>  Quando você compila um assembly (assembly `AssemblyB`) que acessará tipos internos ou membros internos de outro assembly (assembly *A*), deve especificar explicitamente o nome do arquivo de saída (.exe ou .dll) usando a opção do compilador **/out**. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está compilando no momento em que ele está se associando às referências externas. Para obter mais informações, consulte [de entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
```  
  
 Apenas os assemblies que você especificar explicitamente como amigáveis podem acessar os membros e tipos `Friend`. Por exemplo, se o assembly B é um amigo do assembly A e o assembly C faz referência ao assembly B, C não tem acesso aos tipos `Friend` em A.  
  
 O compilador executa algumas validações básicas do nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Se o assembly *A* declara o *B* como um assembly amigável, as regras de validação são as seguintes:  
  
-   Se o assembly *A* for fortemente nomeado, o assembly *B* também deverá ser fortemente nomeado. O nome do assembly amigável passado para o atributo deve consistir no nome do assembly e a chave pública da chave de nome forte usada para assinar o assembly *B*.  
  
     O nome do assembly amigável passado para o atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> não pode ser o nome forte do assembly *B*: não inclua a versão, cultura, arquitetura ou token de chave pública do assembly.  
  
-   Se o assembly *A* não tiver um nome forte, o nome do assembly amigável deverá consistir apenas no nome do assembly. Para obter mais informações, confira [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Se o assembly *B* tiver um nome forte, você deverá especificara a chave de nome forte do assembly *B* usando a configuração do projeto ou a opção do compilador `/keyfile` de linha de comando. Para obter mais informações, confira [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 A classe <xref:System.Security.Permissions.StrongNameIdentityPermission> também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica-se a um tipo individual, enquanto um assembly amigável se aplica ao assembly inteiro.  
  
-   Se há centenas de tipos no assembly *A* que você deseja compartilhar como o assembly *B*, é necessário adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles. Se usar um assembly amigável, você precisará declarar a relação de amigo uma vez.  
  
-   Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você desejar compartilhar precisarão ser declarados como públicos. Se você usar um assembly amigável, os tipos compartilhados serão declarados como `Friend`.  
  
 Para obter informações sobre como acessar um assembly `Friend` tipos e métodos de um arquivo de módulo (um arquivo com a extensão. netmodule), consulte [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Assemblies no .NET](../../../../standard/assembly/index.md)
- [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
