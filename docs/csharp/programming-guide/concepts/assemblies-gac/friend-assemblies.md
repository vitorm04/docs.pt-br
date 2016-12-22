---
title: "Assemblies amig&#225;veis (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Assemblies amig&#225;veis (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *assembly autorizado* é um assembly que pode acessar outro assembly [interno](../../../../csharp/language-reference/keywords/internal.md) tipos e membros. Se você identificar um assembly como um assembly autorizado, você não precisa marcar tipos e membros como público na ordem para que eles sejam acessados por outros assemblies. Isso é especialmente conveniente nas seguintes situações:  
  
-   Durante testes de unidade, quando o código de teste é executado em um assembly separado mas requer acesso a membros no assembly que está sendo testado que são marcados como `internal` .  
  
-   Quando você estiver desenvolvendo uma biblioteca de classes e adições à biblioteca estão contidas em conjuntos separados, mas precisam acessar os membros existentes conjuntos de assemblies que são marcados como `internal` .  
  
## Comentários  
 Você pode usar o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo para identificar um ou mais assemblies amigáveis para um determinado assembly. O exemplo a seguir usa o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> de atributo em um assembly e especifica o assembly `AssemblyB` como um assembly autorizado. Isso permite que o assembly `AssemblyB` acesso a todos os tipos e membros no assembly um que são marcados como `internal`.  
  
> [!NOTE]
>  Quando você compila um assembly \(assembly `AssemblyB`\) que irá acessar tipos internos ou membros internos de outro assembly \(assembly *um*\), você deve especificar explicitamente o nome do arquivo de saída \(.exe ou. dll\) usando o **\/out** opção de compilador. Isso é necessário porque o compilador ainda não gerou o nome do assembly que está construindo no momento em que ele está se ligando referências externas. Para obter mais informações, consulte [\/out \(c\#\)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
```c#  
using System.Runtime.CompilerServices;  
using System;  
  
[assembly: InternalsVisibleTo("AssemblyB")]  
  
// The class is internal by default.  
class FriendClass  
{  
    public void Test()  
    {  
        Console.WriteLine("Sample Class");  
    }  
}  
  
// Public class that has an internal method.  
public class ClassWithFriendMethod  
{  
    internal void Test()  
    {  
        Console.WriteLine("Sample Method");  
    }  
  
}  
```  
  
 Apenas os assemblies que você especificar explicitamente como autorizados podem acessar `internal` tipos e membros. Por exemplo, se o assembly B é um amigo do assembly A e C assembly faz referência ao assembly B, C não tem acesso a `internal` tipos na.  
  
 O compilador executa algumas validações básicas do nome do assembly autorizado passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo. Se assembly *um* declara *B* como um assembly autorizado, as regras de validação são as seguintes:  
  
-   Se assembly *um* for nomeado, assembly forte *B* também deve ser nomeado forte. O nome do assembly autorizado que é passado para o atributo deve conter o nome do assembly e a chave pública da chave de nome forte que é usada para assinar o assembly *B*.  
  
     O nome do assembly autorizado que é passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo não pode ser o nome forte do assembly *B*: não incluem a versão do assembly, cultura, arquitetura ou símbolo de chave pública.  
  
-   Se assembly *um* não for nomeado forte, o nome do assembly autorizado deve consistir apenas o nome do assembly. Para obter mais informações, consulte [Como: Criar Assemblies amigáveis não assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Se assembly *B* for nomeado forte, especifique a chave de nome forte para o assembly *B* usando a configuração do projeto ou da linha de comando `/keyfile` opção de compilador. Para obter mais informações, consulte [Como: Criar Assemblies amigáveis assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 O <xref:System.Security.Permissions.StrongNameIdentityPermission> classe também fornece a capacidade de compartilhar tipos, com as seguintes diferenças:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> aplica\-se a um tipo individual, enquanto um assembly autorizado se aplica a todo o assembly.  
  
-   Se há centenas de tipos no assembly *um* que você deseja compartilhar com assembly *B*, você precisa adicionar <xref:System.Security.Permissions.StrongNameIdentityPermission> a todos eles. Se você usar um assembly autorizado, você precisa declarar a relação de amigo uma vez.  
  
-   Se você usar <xref:System.Security.Permissions.StrongNameIdentityPermission>, os tipos que você deseja compartilhar tem que ser declarado como público. Se você usar um assembly autorizado, os tipos compartilhados são declarados como `internal`.  
  
 Para obter informações sobre como acessar um assembly `internal` tipos e métodos de um arquivo de módulo \(um arquivo com a extensão. netmodule\), consulte [\/moduleassemblyname \(c\#\)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [Como: Criar Assemblies amigáveis não assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [Como: Criar Assemblies amigáveis assinados \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Assemblies e o Cache de Assembly Global \(c\#\)](../../../../csharp/programming-guide/concepts/assemblies-gac/assemblies-and-the-global-assembly-cache.md)   
 [Guia de Programação em C\#](../../../../csharp/programming-guide/index.md)