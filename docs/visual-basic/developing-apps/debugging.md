---
title: "Depurando o aplicativo do Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "depurando [Visual Basic], tarefas comuns"
ms.assetid: 904760b8-9fe9-42a7-9d65-d93774253219
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Depurando o aplicativo do Visual Basic
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Essa página fornece links para a documentação dos recursos de depuração internos do [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)].  Por exemplo, você pode encontrar erros semânticos em seu aplicativo observando seu comportamento em tempo de execução no próprio depurador.  
  
 Usando o depurador, você pode examinar o conteúdo de variáveis em seu aplicativo sem inserir chamadas adicionais para apresentar os valores.  Da mesma forma, você pode inserir um ponto de interrupção no código para interromper a execução no ponto especificado.  
  
## Controlando execução  
 A tabela a seguir lista tarefas de depuração que envolvem controles de execução e fornece links para suas páginas da Ajuda associadas.  
  
|||  
|-|-|  
|Para|Consulte|  
|Inicie para depurar um projeto do Visual Studio, anexe a um processo, divida o código, repasse o código, execute para o cursor, execute para uma função na pilha de chamadas, defina a próxima instrução, repasse o Just My Code, pare a depuração, reinicie a depuração ou desanexe de um processo depurado.|[Navegar pelo Código com o Depurador](/visual-studio/debugger/navigating-through-code-with-the-debugger)|  
|Especifique as configurações para as versões de depuração e de lançamento de um programa.|[Configurações Debug e Release projeto](http://msdn.microsoft.com/pt-br/0440b300-0614-4511-901a-105b771b236e)|  
|Definir opções de início \(argumentos de linha de comando, diretório de trabalho, computador remoto\)|[NIB: How to: Set Start Options for Application Debugging](http://msdn.microsoft.com/pt-br/ce792058-7bac-4dd6-858b-466e872687b8)|  
|Depurar em tempo de design.|[Instruções passo a passo: depurando na hora de design](../Topic/Walkthrough:%20Debugging%20at%20Design%20Time.md)|  
|Habilitar a depuração Just\-in\-Time para iniciar o depurador do Visual Studio quando um programa que está em execução fora do Visual Studio encontra um erro fatal.|[Depuração Just\-In\-Time](/visual-studio/debugger/just-in-time-debugging-in-visual-studio)|  
|Defina pontos de interrupção para linhas de origem, instruções de assembly e função de pilha de chamadas.  Especificar condições, contagens de ocorrências e local de execução.|[Usando pontos de interrupção](/visual-studio/debugger/using-breakpoints)|  
  
## Manipulação de exceções  
 A tabela a seguir lista tarefas de depuração que envolvem manipulação de exceção e aponta para suas páginas da Ajuda associadas.  
  
|||  
|-|-|  
|Para|Consulte|  
|Interromper em exceções sem tratamento.|[Como interromper exceções sem tratamento do usuário](../Topic/How%20to:%20Break%20on%20User-Unhandled%20Exceptions.md)|  
|Interromper quando uma exceção é lançada.|[Como interromper quando uma exceção é lançada](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|Interromper em exceções de primeira tentativa.|[Como interromper quando uma exceção é lançada](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|Usar o assistente de exceção.|[How to: Correct Run\-Time Errors with the Exception Assistant](../Topic/How%20to:%20Correct%20Run-Time%20Errors%20with%20the%20Exception%20Assistant.md)|  
|Adicione uma nova exceção.|[Como adicionar novas exceções](../Topic/How%20to:%20Add%20New%20Exceptions.md)|  
|Continuar a execução após uma exceção ter sido lançada.|[Continuando a execução depois de uma exceção](/visual-studio/debugger/continuing-execution-after-an-exception)|  
  
## Editar e Continuar  
 A tabela a seguir lista tarefas de depuração que envolvem Edição e Continuação e aponta para suas páginas da Ajuda associadas.  
  
|||  
|-|-|  
|Para|Consulte|  
|Desligar e ligar Editar e Continuar.|[Como habilitar e desabilitar Editar e Continuar](../Topic/How%20to:%20Enable%20and%20Disable%20Edit%20and%20Continue.md)|  
|Pare Editar e Continuar de aplicação de alterações de código.|[Como parar alterações no código](../Topic/How%20to:%20Stop%20Code%20Changes.md)|  
|Aplicar edições em modo de interrupção.|[Como aplicar edições no modo de interrupção com editar e continuar](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)|  
  
## Examinando dados de depuração  
 A tabela a seguir lista tarefas de depuração que envolvem visualização de dados de depuração e aponta para suas páginas da Ajuda associadas.  
  
|||  
|-|-|  
|Para|Consulte|  
|Use a janela **Registros** para exibir conteúdo do registro.|[Como usar a janela Registros](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)|  
|Usar a janela **Call Stack** para exibir chamadas de função ou procedimento que estão na pilha.|[Como usar a janela Pilha de Chamadas](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)|  
|Use a janela **Disassembly** para mostrar código assembly correspondente às instruções criadas pelo compilador.|[Como usar a janela Desmontagem](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md)|  
|Use a janela **Módulos** para listar e descrever os módulos usados pelo seu programa.|[Como usar a janela Módulos](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)|  
|Use a janela **Gerenciador de Script** para listar os arquivos de script que estão atualmente carregados no programa.|[Como exibir documentos de script](../Topic/How%20to:%20View%20Script%20Documents.md)|  
|Use a janela **Threads** para examinar e controlar os segmentos \(threads\) no programa.|[Como usar a janela Threads](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)|  
  
## Consulte também  
 [Instruções passo a passo: um Windows Form](../Topic/Walkthrough:%20Debugging%20a%20Windows%20Form.md)   
 [Depurando código gerenciado](/visual-studio/debugger/debugging-managed-code)   
 [Depurando código nativo](/visual-studio/debugger/debugging-native-code)   
 [Depurando aplicativos Web e script](/visual-studio/debugger/debugging-web-applications-and-script)   
 [Referência de interface do usuário de depuração](/visual-studio/debugger/debugging-user-interface-reference)   
 [Configurações de depuração e preparação](/visual-studio/debugger/debugger-settings-and-preparation)   
 [Noções básicas do depurador](/visual-studio/debugger/debugger-basics)   
 [Navegar pelo Código com o Depurador](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [IntelliTrace](/visual-studio/debugger/intellitrace)   
 [Tipos de projeto C\#, F\# e Visual Basic](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [Como aplicar edições no modo de interrupção com editar e continuar](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)