---
title: Estendendo o namespace My no Visual Basic
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25fff04b19cce299a2d437e662fb7481153d29da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Estendendo o namespace My no Visual Basic
O `My` namespace em Visual Basic expõe propriedades e métodos que permitem que você facilmente aproveite a potência do .NET Framework. O `My` namespace simplifica problemas comuns de programação, reduzindo frequentemente uma tarefa difícil para uma única linha de código. Além disso, o `My` namespace é totalmente extensível para que você pode personalizar o comportamento de `My` e adicionar novos serviços para sua hierarquia para adaptar-se às necessidades de aplicativos específicos. Este tópico aborda como personalizar membros existentes da `My` namespace e como adicionar suas próprias classes personalizadas para o `My` namespace.  
  
 **Conteúdo do tópico**  
  
-   [Personalizando meu Namespace membros existentes](#customizing)  
  
-   [Adicionando membros a meus objetos](#addingtoobjects)  
  
-   [Adicionando objetos personalizados para o Meu Namespace](#addingcustom)  
  
-   [Adicionando membros para o My Namespace](#addingtonamespace)  
  
-   [Adicionando eventos a objetos My personalizados](#addingevents)  
  
-   [Diretrizes de design](#design)  
  
-   [Criando bibliotecas de classes para meu](#designing)  
  
-   [Empacotando e implantando extensões](#packaging)  
  
##  <a name="customizing"></a>Personalizando meu Namespace membros existentes  
 O `My` namespace em Visual Basic expõe usados com frequência as informações sobre seu aplicativo, seu computador e muito mais. Para obter uma lista completa dos objetos no `My` namespace, consulte [referência My](../../../visual-basic/language-reference/keywords/my-reference.md). Talvez seja necessário personalizar membros existentes da `My` namespace para que eles melhor atender às necessidades do seu aplicativo. Qualquer propriedade de um objeto de `My` namespace que não é somente leitura pode ser definido como um valor personalizado.  
  
 Por exemplo, suponha que você use com frequência o `My.User` objeto para acessar o contexto de segurança atual para o usuário que executa o aplicativo. No entanto, sua empresa usa um objeto de usuário personalizado para expor informações adicionais e recursos para usuários dentro da empresa. Nesse cenário, você pode substituir o valor padrão de `My.User.CurrentPrincipal` propriedade com uma instância do seu próprio objeto de entidade de segurança personalizada, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Definindo o `CurrentPrincipal` propriedade o `My.User` objeto altera a identidade sob a qual o aplicativo é executado. O `My.User` objeto, por sua vez, retorna informações sobre o usuário especificado mais recentemente.  
  
##  <a name="addingtoobjects"></a>Adicionando membros a meus objetos  
 Os tipos retornados de `My.Application` e `My.Computer` são definidos como `Partial` classes. Portanto, você pode estender o `My.Application` e `My.Computer` objetos criando um `Partial` classe denominada `MyApplication` ou `MyComputer`. A classe não pode ser um `Private` classe. Se você especificar a classe como parte do `My` namespace, você pode adicionar propriedades e métodos que serão incluídos com o `My.Application` ou `My.Computer` objetos.  
  
 Por exemplo, o exemplo a seguir adiciona uma propriedade chamada `DnsServerIPAddresses` para o `My.Computer` objeto.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a>Adicionando objetos personalizados para o Meu Namespace  
 Embora o `My` namespace fornece soluções para muitas tarefas comuns de programação, você poderá encontrar tarefas que o `My` não lida com namespace. Por exemplo, seu aplicativo pode acessar os serviços de diretório personalizado para dados de usuário, ou seu aplicativo pode usar assemblies que não são instalados por padrão com o Visual Basic. Você pode estender o `My` namespace para incluir soluções personalizadas para tarefas comuns que são específicas para seu ambiente. O `My` namespace pode ser facilmente estendido para adicionar novos membros para atender às necessidades crescentes de aplicativo. Além disso, você pode implantar seu `My` extensões de namespace para outros desenvolvedores como um modelo de Visual Basic.  
  
###  <a name="addingtonamespace"></a>Adicionando membros para o My Namespace  
 Porque `My` é um namespace como qualquer outro namespace, você pode adicionar propriedades de nível superior para ele, simplesmente adicionando um módulo e especificando um `Namespace` de `My`. Anote o módulo com o `HideModuleName` atributo conforme mostrado no exemplo a seguir. O `HideModuleName` atributo garante que o IntelliSense não exibirá o nome do módulo quando ele exibe os membros de `My` namespace.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Para adicionar membros a `My` namespace, adicione propriedades conforme necessário para o módulo. Para cada propriedade adicionada para o `My` namespace, adicione um campo particular do tipo `ThreadSafeObjectProvider(Of T)`, onde o tipo é o tipo retornado pela sua propriedade personalizada. Esse campo é usado para criar instâncias de objeto de thread de segurança a ser retornado pela propriedade chamando o `GetInstance` método. Como resultado, cada thread que está acessando a propriedade estendida recebe sua própria instância do tipo retornado. O exemplo a seguir adiciona uma propriedade chamada `SampleExtension` que é do tipo `SampleExtension` para o `My` namespace:  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a>Adicionando eventos a objetos My personalizados  
 Você pode usar o `My.Application` objeto para expor os eventos para personalizados `My` objetos estendendo o `MyApplication` classe parcial no `My` namespace. Para projetos baseados em Windows, você pode clicar duas vezes o **meu projeto** nó para o seu projeto no **Gerenciador de soluções**. No Visual Basic **Project Designer**, clique no `Application` guia e, em seguida, clique no `View Application Events` botão. Será criado um novo arquivo chamado Project. Ele contém o código a seguir para estender o `MyApplication` classe.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Você pode adicionar manipuladores de eventos para personalizados `My` objetos adicionando manipuladores de eventos personalizados para o `MyApplication` classe. Eventos personalizados permitem que você adicione o código que será executado quando um manipulador de eventos é adicionado, removido, ou o evento é gerado. Observe que o `AddHandler` de código para um evento personalizado executado somente se o código é adicionado por um usuário para manipular o evento. Por exemplo, considere que o `SampleExtension` objeto da seção anterior tem um `Load` evento que você deseja adicionar um manipulador de eventos personalizados. O exemplo de código a seguir mostra um manipulador de evento personalizado chamado `SampleExtensionLoad` que será invocado quando o `My.SampleExtension.Load` evento ocorre. Quando o código é adicionado para lidar com o novo `My.SampleExtensionLoad` evento, o `AddHandler` parte desse código de evento personalizado é executado. O `MyApplication_SampleExtensionLoad` método estiver incluído no exemplo de código para mostrar um exemplo de um manipulador de eventos que trata o `My.SampleExtensionLoad` evento. Observe que o `SampleExtensionLoad` eventos estarão disponíveis quando você seleciona o **My Application Events** opção na lista suspensa à esquerda acima do Editor de código quando você estiver editando o arquivo Project.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a>Diretrizes de design  
 Ao desenvolver extensões para o `My` namespace, use as diretrizes a seguir para ajudar a minimizar os custos de manutenção de seus componentes de extensão.  
  
-   **Inclui apenas a lógica de extensão.** A lógica incluída no `My` extensão do namespace deve incluir somente o código que é necessário para expor a funcionalidade necessária no `My` namespace. Como sua extensão residem em projetos de usuário como código-fonte, atualizar o componente de extensão incorre em um custo de manutenção de alta e deve ser evitado se possível.  
  
-   **Minimize as suposições do projeto.** Quando você cria suas extensões do `My` namespace, não presuma um conjunto de referências, importações de nível de projeto ou configurações específicas do compilador (por exemplo, `Option Strict` off). Em vez disso, minimize as dependências e qualificar completamente todas as referências de tipo usando o `Global` palavra-chave. Além disso, certifique-se de que a extensão compila com `Option Strict` em para minimizar os erros na extensão.  
  
-   **Isole o código de extensão.** Colocando o código em um único arquivo torna a extensão mais facilmente implantáveis como um modelo de item do Visual Studio. Para obter mais informações, consulte "Empacotamento e implantação de extensões" posteriormente neste tópico. Colocar todos os a `My` código de extensão do namespace em um único arquivo ou uma pasta separada em um projeto também ajudará os usuários localizar o `My` extensão do namespace.  
  
##  <a name="designing"></a>Criando bibliotecas de classes para meu  
 Como é o caso com a maioria dos modelos de objeto, alguns padrões de design funcionam bem no `My` namespace e outros não. Ao projetar uma extensão para o `My` namespace, considere os seguintes princípios:  
  
-   **Métodos sem monitoração de estado.** Métodos de `My` namespace deve fornecer uma solução completa para uma tarefa específica. Certifique-se de que os valores de parâmetro que são passados para o método fornecem todas as entradas necessárias para concluir uma tarefa específica. Evite criar métodos que se baseiam no estado anterior, como conexões abertas para recursos.  
  
-   **Instâncias globais.** O único estado que é mantido no `My` namespace é global para o projeto. Por exemplo, `My.Application.Info` encapsula o estado que é compartilhado por todo o aplicativo.  
  
-   **Tipos de parâmetro simples.** Manter as coisas simples, evitando tipos complexos de parâmetro. Em vez disso, crie métodos que não tomem nenhum parâmetro de entrada ou que levam tipos simples de entrada como cadeias de caracteres, tipos primitivos e assim por diante.  
  
-   **Métodos de fábrica.** Alguns tipos são necessariamente difíceis de instanciar. Fornecer métodos de fábrica como extensões para o `My` namespace permite que você descubra mais facilmente e consuma tipos que se enquadram nessa categoria. Um exemplo de um método de fábrica que funciona bem é `My.Computer.FileSystem.OpenTextFileReader`. Há vários tipos de fluxo disponíveis no .NET Framework. Especificando arquivos de texto especificamente, o `OpenTextFileReader` ajuda o usuário a entender o fluxo a ser usado.  
  
 Essas diretrizes não eliminam princípios gerais de design para bibliotecas de classe. Em vez disso, eles são recomendações que são otimizadas para desenvolvedores que estão usando o Visual Basic e o `My` namespace. Para princípios gerais de design para criar bibliotecas de classes, consulte [diretrizes de Design do Framework](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a>Empacotando e implantando extensões  
 Você pode incluir `My` extensões do namespace em um modelo de projeto do Visual Studio, ou podem compactar as extensões e implantá-los como um modelo de item do Visual Studio. Ao empacotar sua `My` extensões do namespace como um modelo de item do Visual Studio, você pode tirar proveito dos recursos adicionais fornecidos pelo Visual Basic. Esses recursos permitem que você incluir uma extensão quando um projeto referencia um assembly específico ou permitir que os usuários adicionar explicitamente o `My` extensão do namespace usando o **Minhas extensões** página do Visual Basic Designer de projeto.  
  
 Para obter detalhes sobre como implantar `My` extensões de namespace, consulte [Empacotando e implantando Minhas extensões de personalizado](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Empacotando e implantando minhas extensões personalizadas](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Estendendo o modelo de aplicativo do Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Página Minhas extensões, Designer de projeto](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Parcial](../../../visual-basic/language-reference/modifiers/partial.md)
