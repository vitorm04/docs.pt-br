---
title: "Assemblies amigáveis (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6e01ae91b9d5d875bb618993cd9eda82db59399
ms.lasthandoff: 03/13/2017

---
# <a name="friend-assemblies-visual-basic"></a>Assemblies amigáveis (Visual Basic)
A *assembly autorizado* é um assembly que pode acessar outro assembly [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) tipos e membros. Se você identificar um assembly como um assembly autorizado, você não precisa marcar tipos e membros como público na ordem para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nas seguintes situações:  
  
-   Durante testes de unidade, quando o código de teste é executado em um assembly separado mas requer acesso a membros no assembly que está sendo testado que são marcados como `Friend`.  
  
-   Quando você estiver desenvolvendo uma biblioteca de classes e adições à biblioteca estão contidas em conjuntos separados, mas precisam acessar os membros existentes conjuntos de assemblies que são marcados como `Friend`.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo para identificar um ou mais assemblies amigáveis para um determinado assembly.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> O exemplo a seguir usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>de atributo em um assembly e especifica o assembly `AssemblyB` como um assembly autorizado.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Isso permite que o assembly `AssemblyB` acesso a todos os tipos e membros no assembly um que são marcados como `Friend`.  
  
> [!NOTE]
>  Quando você compila um assembly (assembly `AssemblyB`) que irá acessar tipos internos ou membros internos de outro assembly (assembly *um*), você deve especificar explicitamente o nome do arquivo de saída (.exe ou. dll) usando o **/out** opção de compilador. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está construindo no momento em que ele está se ligando referências externas. Para obter mais informações, consulte [entrada/saída (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
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
  
 Apenas os assemblies que você especificar explicitamente como autorizados podem acessar `Friend` tipos e membros. Por exemplo, se o assembly B é um amigo do assembly A e C assembly faz referência ao assembly B, C não tem acesso a `Friend` tipos na.  
  
 O compilador executa algumas validações básicas do nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Se assembly *um* declara *B* como um assembly autorizado, as regras de validação são as seguintes:  
  
-   Se assembly *um* for nomeado, assembly forte *B* também deve ser nomeado forte. O nome do assembly autorizado que é passado para o atributo deve conter o nome do assembly e a chave pública da chave de nome forte que é usada para assinar o assembly *B*.  
  
     O nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>atributo não pode ser o nome forte do assembly *B*: não incluem a versão do assembly, cultura, arquitetura ou símbolo de chave pública.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
-   Se assembly *um* não for nomeado forte, o nome do assembly autorizado deve consistir apenas o nome do assembly. Para obter mais informações, consulte [como: Criar Assemblies não assinados Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Se assembly *B* for nomeado forte, especifique a chave de nome forte para o assembly *B* usando a configuração do projeto ou da linha de comando `/keyfile` opção de compilador. Para obter mais informações, consulte [como: Criar Assemblies assinados do amigo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 O <xref:System.Security.Permissions.StrongNameIdentityPermission>classe também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>aplica-se a um tipo individual, enquanto um assembly autorizado se aplica a todo o assembly.</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   Se há centenas de tipos no assembly *um* que você deseja compartilhar com assembly *B*, você precisa adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission>a todos eles.</xref:System.Security.Permissions.StrongNameIdentityPermission> Se você usar um assembly autorizado, você precisa declarar a relação de amigo uma vez.  
  
-   Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você deseja compartilhar tem que ser declarado como público.</xref:System.Security.Permissions.StrongNameIdentityPermission> Se você usar um assembly autorizado, os tipos compartilhados são declarados como `Friend`.  
  
 Para obter informações sobre como acessar um assembly `Friend` tipos e métodos de um arquivo de módulo (um arquivo com a extensão. netmodule), consulte [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [Como: Criar Assemblies amigáveis não assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis assinados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
