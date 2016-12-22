---
title: "/win32icon (C# Compiler Options) | Microsoft Docs"
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
  - "/win32icon"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32icon compiler option [C#]"
  - "/win32icon compiler option [C#]"
  - "-win32icon compiler option [C#]"
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /win32icon (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/win32icon** insere um arquivo de .ico no arquivo de saída, que proporciona ao arquivo de saída a aparência desejada no Explorador de Arquivos.  
  
## Sintaxe  
  
```  
/win32icon:filename  
```  
  
## Arguments  
 `filename`  
 O arquivo de .ico que você deseja adicionar ao seu arquivo de saída.  
  
## Comentários  
 Um arquivo de .ico pode ser criado com [Compilador de recursos](http://go.microsoft.com/fwlink/?LinkId=148370).  O compilador de recursos é invocado quando você cria um programa Visual C\+\+; um arquivo de .ico é criado a partir do arquivo de .rc.  
  
 Consulte [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) \(para referenciar\) ou [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) \(\) para anexar um arquivo de recursos do.NET Framework.  Consulte [\/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) para importar um arquivo de .res.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abrir as páginas de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Modifique a propriedade de **Ícone do Aplicativo** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## Exemplo  
 Criar `in.cs` e anexar um arquivo `rf.ico` de .ico para gerar `in.exe`:  
  
```  
csc /win32icon:rf.ico in.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)