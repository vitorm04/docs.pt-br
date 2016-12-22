---
title: "/win32res (C# Compiler Options) | Microsoft Docs"
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
  - "/win32res"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32res compiler option"
  - "/win32res compiler option [C#]"
  - "-win32res compiler option [C#]"
  - "win32res compiler option [C#]"
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /win32res (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/win32res** insere um recurso do Win32 no arquivo de saída.  
  
## Sintaxe  
  
```  
/win32res:filename  
```  
  
## Arguments  
 `filename`  
 O arquivo de recursos que você deseja adicionar ao seu arquivo de saída.  
  
## Comentários  
 Um arquivo de recurso do Win32 pode ser criado com [Compilador de recursos](http://go.microsoft.com/fwlink/?LinkId=148370).  O compilador de recursos é invocado quando você cria um programa Visual C\+\+; um arquivo de .res é criado a partir do arquivo de .rc.  
  
 Um recurso do Win32 pode conter informações da versão ou de bitmap ícone \(\) que ajuda a identificar o seu aplicativo no Explorador de Arquivos.  Se você não especificar **\/win32res**, o compilador gerará as informações de versão com base na versão do assembly.  
  
 Consulte [\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) \(para referenciar\) ou [\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) \(\) para anexar um arquivo de recursos do.NET Framework.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Aplicativo** .  
  
3.  Clique no botão de **Arquivo de recurso** e escolha um arquivo usando a caixa de combinação.  
  
## Exemplo  
 Criar `in.cs` e anexar um arquivo de recursos `rf.res` do Win32 para gerar `in.exe`:  
  
```  
csc /win32res:rf.res in.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)