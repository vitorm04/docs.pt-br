---
title: "/errorreport (C# Compiler Options) | Microsoft Docs"
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
  - "/errorreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-errorreport compiler option [C#]"
  - "errorreport compiler option [C#]"
  - "/errorreport compiler option [C#]"
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
caps.handback.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /errorreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Essa opção fornece um modo conveniente de relatar um erro interno do compilador C\# a Microsoft.  
  
> [!NOTE]
>  No Windows Vista e Windows Server 2008, as configurações de relatório de erros que você usa para Visual Studio não substituem as configurações feitas com o relatório de erros do windows \(WER\).  As configurações de WER sempre têm precedência sobre configurações de relatório de erros do Visual Studio.  
  
## Sintaxe  
  
```  
/errorreport:{ none | prompt | queue | send }  
```  
  
## Arguments  
 **none**  
 Os relatórios sobre erros internos do compilador não serão coletados ou não serão enviados à Microsoft.  
  
 **prompt**  
 Solicita a enviar um relatório quando você receber um erro interno do compilador.  **prompt** é o padrão quando você cria um aplicativo no ambiente de desenvolvimento.  
  
 **queue**  
 Enfileira o relatório de erros.  Quando você faz logon com credenciais administrativas, você pode relatar todas as falhas desde a última vez em que você esteve entrada.  Você não será solicitado a enviar mais de uma vez relatórios para falhas cada três dias.  **queue** é o padrão quando você cria um aplicativo na linha de comando.  
  
 **send**  
 Envia automaticamente relatórios de erros internos do compilador a Microsoft.  Para habilitar essa opção, primeiro você deve concordar com a política de coleta de dados do Microsoft.  A primeira vez que você especifica **\/errorreport:send** em um computador, uma mensagem do compilador referir\-lhe\-á um site que contém a política de coleta de dados do Microsoft.  
  
 Essa opção depende das configurações do Registro.  Para obter informações sobre como definir os valores apropriados no Registro, consulte [Como ativar o relatório automático de erros em ferramentas de linha de comando do Visual Studio 2008](http://go.microsoft.com/fwlink/?LinkID=184695) no site do MSDN.  
  
## Comentários  
 Um erro interno \(ICE\) do compilador resultados quando o compilador não pode processar um arquivo de código\-fonte.  Quando um GELO ocorre, o compilador não gerencia um arquivo de saída ou nenhum de diagnóstico úteis que você pode usar para corrigir seu código.  
  
 Em versões anteriores, quando você recebeu um GELO, você tenha incentivado contate chamada Microsoft para informar o problema.  Usando **\/errorreport**, você pode fornecer informações de GELO a equipe do Visual C \#.  Os relatórios de erros podem ajudar a melhorar versões futuras do compilador.  
  
 A capacidade de um usuário de enviar relatórios depende das permissões de política do computador e do usuário.  
  
 Para obter mais informações sobre o depurador de erro, consulte [Descrição dr. Watson. para a ferramenta do windows \(Drwtsn32.exe\)](http://go.microsoft.com/fwlink/?LinkId=147286).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  Para obter mais informações, consulte [Página de Compilação, Designer de Projeto \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Relatório de Erros do Compilador Interno** .  
  
 Para obter informações sobre como configurar esta opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)