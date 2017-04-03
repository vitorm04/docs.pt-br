---
title: "/moduleassemblyname (Opção do Compilador de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /moduleassemblyname
dev_langs:
- CSharp
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d8c65394374ce3360461ad64b9cfc3353b79e0a7
ms.lasthandoff: 03/13/2017

---
# <a name="moduleassemblyname-c-compiler-option"></a>/moduleassemblyname (Opção do compilador de C#)
Especifica um assembly cujos tipos não públicos podem ser acessados por um .netmodule.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 O nome do assembly cujos tipos não públicos podem ser acessados por um .netmodule.  
  
## <a name="remarks"></a>Comentários  
 O **/moduleassemblyname** deverá ser usado ao compilar um .netmodule e quando as condições a seguir forem true:  
  
-   O .netmodule precisa acessar tipos não públicos em um assembly existente.  
  
-   Você sabe o nome do assembly no qual o .netmodule será compilado.  
  
-   O assembly existente concedeu acesso de assembly amigável ao assembly no qual o .netmodule será compilado.  
  
 Para obter mais informações sobre a compilação de um .netmodule, consulte [/target:module (Opções do Compilador C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Para obter mais informações sobre assemblies amigos, consulte [Assemblies Amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
 Essa opção não está disponível de dentro do ambiente de desenvolvimento; ela só está disponível quando se compila na linha de comando.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo compila um assembly com um tipo privado que concede acesso de assembly amigável a um assembly denominado csman_an_assembly.  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo compila um .netmodule que acessa um tipo não público no assembly moduleassemblyname_1.dll. Sabendo que esse .netmodule será compilado dentro de um assembly chamado csman_an_assembly, é possível especificar **/moduleassemblyname**, permitindo que o .netmodule acesse tipos não públicos em um assembly que tenha concedido acesso de assembly amigável ao csman_an_assembly.  
  
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
  
## <a name="example"></a>Exemplo  
 Este exemplo de código compila o assembly csman_an_assembly, referenciando o assembly compilado anteriormente e o .netmodule.  
  
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
  
 **An_Internal_Class.Test foi chamado**   
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
