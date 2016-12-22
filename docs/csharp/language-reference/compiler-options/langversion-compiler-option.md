---
title: "/langversion (C# Compiler Options) | Microsoft Docs"
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
  - "/langversion"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/langversion compiler option [C#]"
  - "-langversion compiler option [C#]"
  - "langversion compiler option [C#]"
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
caps.handback.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /langversion (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Faz com que o compilador aceita apenas a sintaxe que é incluída na especificação escolhida de linguagem C\#.  
  
## Sintaxe  
  
```  
/langversion:option  
```  
  
## Arguments  
 `option`  
 Os seguintes valores são válidos:  
  
|Opção|Significado|  
|-----------|-----------------|  
|default|O compilador aceita qualquer sintaxe de idioma válido.|  
|ISO\-1|O compilador só aceita sintaxe que é incluída na especificação de linguagem C\# 23270:2003 do PADRÃO.|  
|ISO\-2|O compilador só aceita sintaxe que é incluída na especificação de linguagem C\# 23270:2006 do PADRÃO.  Essa especificação está disponível [ISO](http://go.microsoft.com/fwlink/?LinkId=144406) no site.|  
|3|O compilador só aceita sintaxe que é incluída na versão 3,0 [Especificação da linguagem C\#](../../../visual-basic/reference/language-specification.md).|  
  
## Comentários  
 Os metadados referenciados por seu aplicativo C\# não estão sujeitos à opção do compilador de **\/langversion** .  
  
 Como cada versão do compilador C\# contém extensões para a especificação de idioma, **\/langversion** ele não oferece a funcionalidade equivalente de uma versão anterior do compilador.  
  
 Independentemente de qual **\/langversion** definir o uso, você usará a versão atual do Common Language Runtime para criar o .exe ou .dll.  Uma exceção é os assemblies e o [\/moduleassemblyname \(Specify Friend Assembly for Module\)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)de amigo, que funcionam em **\/langversion:ISO\-1**.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Versão da Linguagem** .  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Especificação da linguagem C\#](../../../visual-basic/reference/language-specification.md)