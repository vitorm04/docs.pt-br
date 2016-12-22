---
title: "/lib (C# Compiler Options) | Microsoft Docs"
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
  - "/lib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lib compiler option [C#]"
  - "-lib compiler option [C#]"
  - "/lib compiler option [C#]"
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /lib (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/lib** especifica o local dos assemblies referenciados por meio da opção de [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) .  
  
## Sintaxe  
  
```  
/lib:dir1[,dir2]  
```  
  
## Arguments  
 `dir1`  
 Um diretório para que o compilador examinar se um assembly referenciado não for localizado no diretório de trabalho atual \(o diretório do qual você estiver invocando o compilador\) ou no diretório do sistema de Common Language Runtime.  
  
 `dir2`  
 Um ou vários diretórios adicionais para pesquisar em por referências de assembly.  Separar nomes de diretório adicionais com uma vírgula, e sem espaço em branco entre eles.  
  
## Comentários  
 O compilador procura por referências de montagem que não correspondem completamente às exigências na seguinte ordem:  
  
1.  Diretório de trabalho corrente.  Este é o diretório do qual o compilador é chamado.  
  
2.  O diretório do sistema common language runtime.  
  
3.  Diretórios especificados por **\/lib**.  
  
4.  Diretórios especificados pela variável de ambiente LIB.  
  
 Use **\/reference** para especificar uma referência de assembly.  
  
 **\/lib** é suplementares; especificando ao anexar mais de uma vez para todos os valores anteriores.  
  
 Uma alternativa ao uso **\/lib** é copiar no diretório de trabalho todos os assemblies necessários; isso permitirá que você transmite apenas o nome do assembly a **\/reference**.  É possível excluir os assemblies do diretório de trabalho.  Desde que o caminho para o assembly dependente não é especificado no manifesto do assembly, o aplicativo pode ser iniciado no computador de destino e encontrará e usará o assembly em cachê de assembly global.  
  
 Como o compilador pode fazer referência ao assembly não implica Common Language Runtime poderá localizar e carregar o assembly em tempo de execução.  Consulte [Como o tempo de execução localiza assemblies](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md) para obter detalhes sobre como o tempo de execução pesquisa pelos assemblies referenciados.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a caixa de diálogo **Páginas de Propriedade** do projeto.  
  
2.  Clique na página de propriedades de **Caminho de Referências** .  
  
3.  Modifique o conteúdo da caixa de listagem.  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## Exemplo  
 Criar t2.cs para criar um arquivo .exe.  O compilador será no diretório de trabalho e o diretório raiz da unidade C para referências de assembly.  
  
```  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)