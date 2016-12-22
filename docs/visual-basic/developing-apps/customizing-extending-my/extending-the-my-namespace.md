---
title: "Estendendo o namespace My no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.AddingMyExtensions"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Meu namespace"
  - "Meu namespace, personalizando"
  - "Meu namespace, estendendo"
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estendendo o namespace My no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O namespace `My` em Visual Basic expõe propriedades e métodos que permitem que você facilmente aproveite o poder do .NET Framework.  O namespace `My` simplifica problemas comuns de programação, reduzindo frequentemente uma tarefa difícil para uma única linha de código.  Além disso, o namespace `My` é totalmente extensível para que você pode personalizar o comportamento de `My` e adicionar novos serviços para sua hierarquia para adaptar\-se às necessidades de aplicativos específicos.  Este tópico aborda como personalizar membros existentes do namespace `My` e como adicionar suas próprias classes personalizadas ao namespace `My`.  
  
 **Conteúdo do Tópico**  
  
-   [Personalizando membros existentes do Namespace My](#customizing)  
  
-   [Adicionando membros a meus objetos](#addingtoobjects)  
  
-   [Adicionando objetos personalizados para o Namespace My](#addingcustom)  
  
-   [Adicionando membros para o My Namespace](#addingtonamespace)  
  
-   [Adicionar eventos a objetos My personalizados](#addingevents)  
  
-   [Diretrizes de Design](#design)  
  
-   [Projetando bibliotecas de classes para My](#designing)  
  
-   [Compactação e implantação de Extensões](#packaging)  
  
##  <a name="customizing"></a> Personalizando membros existentes do Namespace My  
 O namespace `My` em Visual Basic expõe informações usadas com frequência sobre seu aplicativo, seu computador e mais.  Para obter uma lista completa dos objetos no namespace `My`, consulte [Minha referência](../../../visual-basic/language-reference/keywords/my-reference.md).  Talvez você precise personalizar membros existentes do namespace `My` de forma que combinem melhor com as necessidades do seu aplicativo.  Qualquer propriedade de um objeto no namespace `My` que é não somente leitura pode ser definida para um valor personalizado.  
  
 Por exemplo, suponha que você frequentemente use o objeto `My.User` para acessar o contexto de segurança atual para o usuário que estiver executando o aplicativo.  No entanto, sua empresa usa um objeto de usuário personalizado para expor informações adicionais e recursos para usuários dentro da empresa.  Nesse cenário, você pode substituir o valor padrão da propriedade `My.User.CurrentPrincipal` com uma instância do seu próprio objeto principal personalizado, como mostrado no exemplo o seguir.  
  
 [!CODE [VbVbcnExtendingMy#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#1)]  
  
 Configurando a propriedade `CurrentPrincipal` sobre os objetos`My.User` altera a identidade na qual o aplicativo é executado.  O objeto `My.User`, por sua vez, retorna informações sobre o usuário recém\-especificado.  
  
##  <a name="addingtoobjects"></a> Adicionando membros a meus objetos  
 Os tipos retornados de `My.Application` e `My.Computer` são definidos como classes `Partial`.  Portanto, você pode estender os objetos `My.Application` e objetos `My.Computer` criando uma  classe `Partial` de nome `MyApplication` ou `MyComputer`.  A classe não pode ser uma classe `Private`.  Se você especificar a classe como parte do namespace `My`, você pode adicionar propriedades e métodos que serão incluídos com os objetos `My.Application` ou `My.Computer`.  
  
 Por exemplo, o exemplo a seguir adiciona uma propriedade chamada `DnsServerIPAddresses` ao objeto `My.Computer`.  
  
 [!CODE [VbVbcnExtendingMy#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#2)]  
  
##  <a name="addingcustom"></a> Adicionando objetos personalizados para o Namespace My  
 Embora o namespace `My` forneça soluções para várias tarefas comuns de programação, você poderá encontrar tarefas que o namespace `My` não aborda.  Por exemplo, seu aplicativo pode acessar serviços de diretório personalizados para dados de usuário, ou seu aplicativo pode usar assemblies que não são instalados por padrão com Visual Basic.  Você pode estender o namespace `My` para incluir soluções personalizadas para tarefas comuns que são específicas para seu ambiente.  O namespace `My` facilmente pode ser estendido para adicionar novos membros para atender às crescentes necessidades do aplicativo.  Além disso, você pode implantar suas extensões do namespace `My` para outros desenvolvedores como um modelo Visual Basic.  
  
###  <a name="addingtonamespace"></a> Adicionando membros para o My Namespace  
 Como `My` é namespace como qualquer outro namespace, você pode adicionar propriedades de nível superior para ele, simplesmente adicionando um módulo e especificando um `Namespace` de `My`.  Anote o módulo com o atributo `HideModuleName` conforme mostrado no exemplo o seguir.  O atributo `HideModuleName` assegura que o Intellisense não exibirá o nome do módulo quando ele exibe os membros do namespace `My`.  
  
 [!CODE [VbVbcnExtendingMy#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#3)]  
  
 Para adicionar membros ao namespace `My`, adicione propriedades conforme necessário para o módulo.  Para cada propriedade adicionada ao namespace `My`, adicione um campo particular do tipo `ThreadSafeObjectProvider(Of T)`, onde o tipo é o tipo retornado pela sua propriedade personalizada.  Este campo é usado para criar instâncias do objeto de thread de segurança a ser retornado pela propriedade chamando o método `GetInstance`.  Como resultado, cada thread que está acessando a propriedade estendida recebe sua própria instância do tipo retornado.  O exemplo a seguir adiciona uma propriedade chamada `SampleExtension` que é do tipo `SampleExtension` ao namespace `My`:  
  
 [!CODE [VbVbcnExtendingMy#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#4)]  
  
##  <a name="addingevents"></a> Adicionar eventos a objetos My personalizados  
 Você pode usar o objeto `My.Application` para expor os eventos para os seus objetos `My` personalizados estendendo a classe parcial  `MyApplication` no namespace`My`.  Para projetos baseados no Windows, você pode clicar duas vezes o nó  **My Project**  para o seu projeto em **Solution Explorer**.  Na Visual Basic  **Project Designer** ,clique na guia `Application` e, em seguida, clique no botão `View Application Events`.  Um novo arquivo chamado ApplicationEvents.vb será criado.  Ele contém o código a seguir para estender a classe `MyApplication`.  
  
 [!CODE [VbVbcnExtendingMy#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#5)]  
  
 Você pode adicionar manipuladores de eventos para os seus objetos `My` personalizados adicionando a classe `MyApplication` de manipuladores de eventos personalizados.  Eventos personalizados permitem que você adicione um código que será executado quando um manipulador de eventos é adicionado, removido, ou o evento é gerado.  Observe que o código `AddHandler` de um evento personalizado executado somente se o código é adicionado por um usuário para manipular o evento.  Por exemplo, considere que o objeto `SampleExtension` da seção anterior tem um evento `Load` para o qual você deseja adicionar um manipulador de eventos personalizado.  O exemplo de código a seguir mostra um manipulador de eventos personalizado chamado `SampleExtensionLoad` que será chamado quando o evento `My.SampleExtension.Load` ocorrer.  Quando o código é adicionado para manipular o novo evento `My.SampleExtensionLoad`, a parte `AddHandler` deste código personalizado de evento é executada.  O método `MyApplication_SampleExtensionLoad` está incluído no exemplo de código para mostrar um exemplo de uma manipulador de eventos que manipula o evento `My.SampleExtensionLoad`.  Observe que o evento `SampleExtensionLoad` estará disponível quando você selecionar a opção **My Application Events** em uma lista suspensa a esquerda acima do editor de código quando você estiver editando o arquivo ApplicationEvents.vb.  
  
 [!CODE [VbVbcnExtendingMy#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnExtendingMy#6)]  
  
##  <a name="design"></a> Diretrizes de Design  
 Ao desenvolver extensões para o namespace `My`, use as diretrizes a seguir para ajudar a minimizar os custos de manutenção de seus componentes de extensão.  
  
-   **Inclua somente a extensão lógica.** A lógica incluída na `My` extensão namespace deve incluir somente o código necessário para expor a funcionalidade necessária na `My` espaço para nome.  Porque sua extensão será residente em projetos de usuário como código\-fonte, atualizando o componente de extensão provoca um custo alto de manutenção e deve ser evitado se possível.  
  
-   **Minimize as suposições do projeto.** Quando você cria suas extensões da `My` espaço para nome, não pressuponha que um conjunto de referências, imports de nível de projeto ou configurações do compilador específico \(por exemplo, `Option Strict` off\).  Em vez disso, minimize as dependências e qualifique totalmente todas as referências de tipo usando a palavra\-chave `Global`.  Além disso, certifique\-se de que a extensão compila com `Option Strict` para reduzir erros na extensão.  
  
-   **Isole o código de extensão.** Colocando o código em um único arquivo torna a extensão mais facilmente implantáveis como um modelo de item de Visual Studio.  Para obter mais informações, consulte "Compactação e implantação de Extensões" posteriormente contidas neste tópico.  Colocando todo o código da extensão do namespace `My` em um único arquivo ou uma pasta separada em um projeto também ajudará os usuários a localizar a extensão do namespace `My`.  
  
##  <a name="designing"></a> Projetando bibliotecas de classes para My  
 Como é o caso com a maioria dos modelos de objeto, alguns padrões de design funcionam bem no namespace `My` e outros não.  Ao projetar uma extensão para o namespace `My`, considere os seguintes princípios:  
  
-   **Métodos sem\-estado.** Métodos de `My` namespace deve fornecer uma solução completa para uma tarefa específica.  Certifique\-se que os valores de parâmetro que são passados para o método fornecem todas as entradas necessárias para concluir uma tarefa específica.  Evite a criação de métodos que se baseiam no estado anterior, como conexões abertas para recursos.  
  
-   **Instâncias globais.** O estado único que é mantido na `My` espaço para nome é global para o projeto.  Por exemplo, `My.Application.Info` encapsula o estado que é compartilhado em todo o aplicativo.  
  
-   **Tipos de parâmetro simples.** Mantenha as coisas simples, evitando tipos complexos de parâmetro.  Em vez disso, crie métodos que não tomem nenhum parâmetro de entrada ou que levam tipos simples de entrada como sequências de caracteres, tipos primitivos e assim por diante.  
  
-   **Métodos de fábrica.** Alguns tipos são necessariamente difíceis de instanciar.  Fornecer métodos de fábrica como extensões ao namespace `My` permite que você mais facilmente descobra e consuma tipos que se enquadram nessa categoria.  Um exemplo de um método de fábrica que funciona bem é `My.Computer.FileSystem.OpenTextFileReader`.  Há vários tipos de fluxo disponíveis no .NET Framework.  Especificando arquivos de texto especificamente, a ajuda ao usuário `OpenTextFileReader` compreende qual fluxo a ser usado.  
  
 Essas diretrizes não eliminam princípios gerais de design para bibliotecas de classes.  Em vez disso, eles são recomendações que são otimizadas para os desenvolvedores que estiverem usando Visual Basic e o namespace `My`.  Para princípios gerais de design para criar bibliotecas de classes, consulte [Diretrizes de Design de estrutura](../Topic/Framework%20Design%20Guidelines.md).  
  
##  <a name="packaging"></a> Compactação e implantação de Extensões  
 Você pode incluir extensões de namespace `My` em um modelo de projeto Visual Studio, ou pode compactar as extensões e implantá\-los como um modelo de item de Visual Studio.  Quando você compacta as extensões de namespace `My` como um modelo de item Visual Studio, você pode aproveitar recursos adicionais fornecidos pelo Visual Basic.  Esses recursos permitem que você incluía uma extensão quando um projeto referencia um assembly específico, ou habilita usuários para adicionar suas extensões de namespace `My` explicitamente, usando a página **My Extensions** do Project Designer do Visual Basic.  
  
 Para obter detalhes sobre como implantar as extensões de namespace `My`, consulte [Empacotando e implantando minhas extensões personalizadas](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## Consulte também  
 [Empacotando e implantando minhas extensões personalizadas](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Página Minhas Extensões, Designer de Projeto](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Parcial](../../../visual-basic/language-reference/modifiers/partial.md)