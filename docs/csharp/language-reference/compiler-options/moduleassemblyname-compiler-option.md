---
title: "/moduleassemblyname (C# Compiler Option) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/moduleassemblyname"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "moduleassemblyname compiler option [C#]"
  - "/moduleassemblyname compiler option [C#]"
  - ".moduleassemblyname compiler option [C#]"
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /moduleassemblyname (C# Compiler Option)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica um assembly cujo não público digitar um .netmodule pode acessar.  
  
## Sintaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Arguments  
 `assembly_name`  
 O nome do assembly cujo não utilitário no .netmodule pode acessar.  
  
## Comentários  
 **\/moduleassemblyname** deve ser usado ao criar um .netmodule, e quando as seguintes condições forem verdadeiras:  
  
-   O acesso das necessidades de .netmodule como não utilitário em um assembly existente.  
  
-   Você souber o nome do assembly no qual o .netmodule será criado.  
  
-   O assembly existente concedeu acesso do assembly de amigo ao assembly no qual o .netmodule será criado.  
  
 Para obter mais informações sobre como criar um .netmodule, consulte [\/target:module \(Create Module to Add to Assembly\)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Para obter mais informações sobre os assemblies de amigo, consulte [Assemblies amigáveis](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Essa opção não está disponível dentro do ambiente de desenvolvimento; está disponível apenas durante a criação de linha de comando.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
## Exemplo  
 Este exemplo cria um assembly com um tipo particular, e que concede acesso do assembly de amigo a um assembly chamado csman\_an\_assembly.  
  
```  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## Exemplo  
 Este exemplo cria um .netmodule que acessa um utilitário não tenha o assembly moduleassemblyname\_1.dll.  Sabendo que este .netmodule será construído em um assembly chamado csman\_an\_assembly, é possível especificar **\/moduleassemblyname**, permitindo que o .netmodule acessa o utilitário não em um assembly que concedesse acesso do assembly de amigo a csman\_an\_assembly.  
  
```  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## Exemplo  
 Este exemplo de código cria o assembly csman\_an\_assembly, a referência ao assembly e o .netmodule anteriormente compilados.  
  
```  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
  **Chamado An\_Internal\_Class.Test**   
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)