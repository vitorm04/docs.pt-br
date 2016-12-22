---
title: "/keyfile (C# Compiler Options) | Microsoft Docs"
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
  - "/keyfile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keyfile compiler option [C#]"
  - "-keyfile compiler option [C#]"
  - "keyfile compiler option [C#]"
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /keyfile (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica o nome do arquivo que contém a chave de criptografia.  
  
## Sintaxe  
  
```  
/keyfile:file  
```  
  
## Arguments  
  
|Termo|Definição|  
|-----------|---------------|  
|`file`|O nome do arquivo que contém a chave de nome forte.|  
  
## Comentários  
 Quando essa opção é usada, o compilador insere a chave pública do arquivo especificado no manifesto do assembly e assinar o assembly final com a chave privada.  Para gerar um arquivo de chave, digite o sn \- k `file` na linha de comando.  
  
 Se você compila com **\/target:module**, o nome do arquivo da chave será realizado no módulo e inserida no assembly que é criado quando você cria um assembly com [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Você também pode transmitir suas informações de criptografia ao compilador com [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  Use [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se você desejar um assembly parcialmente assinado.  
  
 No caso de \/keyfile e \/keycontainer são especificados \(a opção de linha de comando ou pelo atributo personalizado\) na mesma compilação, o compilador primeiro tentará o contêiner de chave.  Se isso for bem\-sucedida, o assembly é assinado com as informações do contêiner de chave.  Se o compilador não localizar o contêiner de chave, o tentará o arquivo especificado com a \/keyfile.  Se isso ocorrer, o assembly é assinado com as informações do arquivo de chave e as informações fundamentais será instalado no contêiner de chave \(semelhantemente a sn \- i\) de forma que na compilação seguir, o contêiner chave é válido.  
  
 Observe que um arquivo de chave pode conter apenas a chave pública.  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nome forte](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) e [Atrasando a assinatura de um assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** para o projeto.  
  
2.  Clique na página de propriedades de **Assinando** .  
  
3.  Modifique a propriedade de **Escolha um arquivo de chave de nome forte** .  
  
 Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)