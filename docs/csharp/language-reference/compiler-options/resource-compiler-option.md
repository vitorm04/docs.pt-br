---
title: "/resource (C# Compiler Options) | Microsoft Docs"
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
  - "/resource"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-resource compiler option [C#]"
  - "/resource compiler option [C#]"
  - "-res compiler option [C#]"
  - "/res compiler option [C#]"
  - "res compiler option [C#]"
  - "resource compiler option [C#]"
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /resource (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Insere o recurso especificado no arquivo de saída.  
  
## Sintaxe  
  
```  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## Arguments  
 `filename`  
 O arquivo de recursos do.NET Framework que você deseja inserir no arquivo de saída.  
  
 `identifier` \(opcional\)  
 O nome lógico do recurso; o nome usado para carregar o recurso.  O padrão é o nome de arquivo.  
  
 `accessibility-modifier` \(opcional\)  
 A facilidade de uso de recursos: público ou particular.  A opção é pública.  
  
## Comentários  
 Use [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) para vincular um recurso a um assembly e não adicione o arquivo de recurso no arquivo de saída.  
  
 Por padrão, os recursos são públicos no assembly quando são criados usando o compilador C\#.  Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade.  Nenhuma outra acessibilidade a não ser `public` ou `private` é permitida.  
  
 Se `filename` é um arquivo de recursos do .NET Framework criado, por exemplo, por [Resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md) ou no ambiente de desenvolvimento, pode ser acessado com membros do namespace <xref:System.Resources> .  Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=fullName>.  Para todos recursos demais, use `GetManifestResource`\* métodos na classe de <xref:System.Reflection.Assembly> para acessar em tempo de execução do recurso.  
  
 **\/res** é a forma abreviada de **\/resource**.  
  
 A ordem dos recursos no arquivo de saída é determinado da ordem especificada na linha de comando.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Adicionar um arquivo de recurso ao seu projeto.  
  
2.  Selecione o arquivo que você deseja inserir em **Gerenciador de Soluções**.  
  
3.  Selecione para **Ação de Compilação** o arquivo na janela de **Propriedades** .  
  
4.  Definir **Ação de Compilação** a **Recurso Inserido**.  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## Exemplo  
 Criar `in.cs` e anexar o arquivo de recursos `rf.resource`:  
  
```  
csc /resource:rf.resource in.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)