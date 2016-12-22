---
title: "/debug (C# Compiler Options) | Microsoft Docs"
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
  - "/debug"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "debug compiler option [C#]"
  - "-debug compiler option [C#]"
  - "/debug compiler option [C#]"
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /debug (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/debug** faz com que o compilador gerencia informações de depuração e a colocará no arquivo de saída ou nos arquivos.  
  
## Sintaxe  
  
```  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## Arguments  
 `+` &#124; `-`  
 Especificando `+`, ou apenas **\/debug**, faz o compilador gerar informações de depuração e a colocará em uma base de dados do programa \(arquivo .pdb\).  Especificar `-`, que é aplicado se você não especificar **\/debug**, não cria nenhuma informação de depuração.  
  
 `full` &#124; `pdbonly`  
 Especifica o tipo de informações de depuração gerado pelo compilador.  O argumento completo, que é aplicado se você não especificar **\/debug:pdbonly**, permite anexar um depurador ao programa em execução.  Especifique pdbonly permite a depuração do código\-fonte quando o programa for iniciado no depurador mas só exibirá o assembler quando o programa em execução é anexado ao depurador.  
  
## Comentários  
 Use esta opção para criar construções de depuração.  Se **\/debug**, **\/debug\+**, ou **\/debug:full** não são especificados, você não poderá depurar o arquivo de saída do programa.  
  
 Se você usar **\/debug:full**, lembre\-se de que há algum impacto na velocidade e o tamanho de código otimizado JIT e um impacto pequeno na qualidade de código com **\/debug:full**.  Não recomendamos **\/debug:pdbonly** ou nenhum PDB para gerar o código da versão.  
  
> [!NOTE]
>  Uma diferença entre **\/debug:pdbonly** e **\/debug:full** é a **\/debug:full** com que o compilador emite <xref:System.Diagnostics.DebuggableAttribute>, que é usado para informar o compilador JIT de depuração da informação está disponível.  Em virtude disso, você obterá um erro se seu código contém <xref:System.Diagnostics.DebuggableAttribute> definido como false se você usar **\/debug:full**.  
  
 Para obter mais informações sobre como configurar o desempenho de depuração de um aplicativo, consulte [Facilitando uma imagem depuração](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  
  
 Para alterar o local do arquivo .pdb, consulte [\/pdb \(Specify Debug Symbol File\)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Informações de Depuração** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## Exemplo  
 Colocar informações de depuração no arquivo de saída `app.pdb`:  
  
```  
csc /debug /pdb:app.pdb test.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)