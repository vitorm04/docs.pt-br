---
title: "/linkresource (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/linkresource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/linkresource compiler option [C#]"
  - "linkres compiler option [C#]"
  - "/linkres compiler option [C#]"
  - "-linkres compiler option [C#]"
  - "-linkresource compiler option [C#]"
  - "linkresource compiler option [C#]"
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /linkresource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cria um link para um recurso do .NET Framework no arquivo de saída.  O arquivo de recursos que não é adicionado ao arquivo de saída.  Isso difere da opção de [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) que insere um arquivo de recursos no arquivo de saída.  
  
## Sintaxe  
  
```  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 O arquivo de recursos do .NET Framework à qual você deseja vincular do assembly.  
  
 `identifier` \(opcional\)  
 O nome lógico do recurso; o nome usado para carregar o recurso.  O padrão é o nome do arquivo.  
  
 `accessibility-modifier` \(opcional\)  
 A facilidade de uso de recursos: público ou particular.  A opção é pública.  
  
## Comentários  
 Por padrão, os recursos vinculados são públicos no assembly quando são criados com o compilador C\#.  Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.  É permitido em qualquer outro modificador a não ser `public` ou `private` .  
  
 **\/linkresource** exige uma das opções de [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de **\/target:module**.  
  
 Se `filename` é um arquivo de recursos do .NET Framework criado, por exemplo, por [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou no ambiente de desenvolvimento, pode ser acessado com membros do namespace <xref:System.Resources> .  Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=fullName>.  Para todos recursos demais, use `GetManifestResource`\* métodos na classe de <xref:System.Reflection.Assembly> para acessar em tempo de execução do recurso.  
  
 O arquivo especificado em `filename` pode ser qualquer formato.  Por exemplo, talvez você queira fazer parte de DLL nativa do assembly, de modo que possa ser instalado em cachê de assembly global e ser acessado de código gerenciado no assembly.  O segundo nos exemplos a seguir mostra como fazer isso.  Você pode fazer a mesma coisa no vinculador do assembly.  O terceiro dos exemplos a seguir mostra como fazer isso.  Para obter mais informações, consulte [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) e [Trabalhando com assemblies e o cache de assemblies global](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md).  
  
 **\/linkres** é a forma abreviada de **\/linkresource**.  
  
 Essa opção do compilador não estiver disponível no Visual Studio e não pode ser modificada programaticamente.  
  
## Exemplo  
 Criar `in.cs` e links no arquivo de recurso `rf.resource`:  
  
```  
csc /linkresource:rf.resource in.cs  
```  
  
## Exemplo  
 Criar `A.cs` em uma DLL, um link a DLL nativa N.dll, e coloca a saída em cachê de assembly global \(GAC\).  Neste exemplo, A.dll e N.dll irão residir no GAC.  
  
```  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## Exemplo  
 Este exemplo faz a mesma coisa que anterior, mas usando opções do vinculador do assembly.  
  
```  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Trabalhando com assemblies e o cache de assemblies global](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)