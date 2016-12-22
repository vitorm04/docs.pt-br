---
title: "/filealign (C# Compiler Options) | Microsoft Docs"
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
  - "/filealign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/alignment compiler option [C#]"
  - "filealign compiler option [C#]"
  - "-filealign compiler option [C#]"
  - "/sections compiler option [C#]"
  - "alignment compiler option [C#]"
  - "sections compiler option [C#]"
  - "-sections compiler option [C#]"
  - "/filealign compiler option [C#]"
  - "file sharing [C#]"
  - "-alignment compiler option [C#]"
  - "section alignment [C#]"
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /filealign (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/filealign** permite especificar o tamanho das seções a seguir em seu arquivo de saída.  
  
## Sintaxe  
  
```  
/filealign:number  
```  
  
## Arguments  
 `number`  
 Um valor que especifica o tamanho das seções no arquivo de saída.  Os valores válidos são 512, 1024, 2048, 4096, e 8192.  Esses valores estão em bytes.  
  
## Comentários  
 Cada seção será alinhado em um limite que é um múltiplo do valor de **\/filealign** .  Não há nenhuma opção fixa.  Se **\/filealign** não for especificado, Common Language Runtime escolher uma opção em tempo de compilação.  
  
 Especificando o tamanho da seção, isso afeta o tamanho do arquivo de saída.  O tamanho da seção pode ser útil para programas que serão executadas em dispositivos menores.  
  
 Use [DUMPBIN](/visual-cpp/build/reference/dumpbin-options) para consultar informações sobre seções a seguir em seu arquivo de saída.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Alinhamento de Arquivo** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)