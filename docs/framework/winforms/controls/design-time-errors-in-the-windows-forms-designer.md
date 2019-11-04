---
title: Erros de tempo de design no Designer de Formulários do Windows
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0dd112f89071f6981b438a79f350dfab02af73d5
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460113"
---
# <a name="windows-forms-designer-error-page"></a>Designer de Formulários do Windows página de erro

Se a Designer de Formulários do Windows não for carregada devido a um erro em seu código, em um componente de terceiros ou em outro lugar, você verá uma página de erro em vez do designer. Essa página de erro não significa necessariamente um bug no designer. O bug pode estar em algum lugar na página code-behind chamada \<nome-do-formulário >. Designer.cs. Os erros aparecem nas barras recolhíveis e amarelas com um link para saltar para o local do erro na página de código.

![Designer de Formulários do Windows página de erro](media/windows-forms-designer-error-page-collapsed.png)

Você pode optar por ignorar os erros e continuar carregando o Designer clicando em **ignorar e continuar**. Essa ação pode resultar em um comportamento inesperado, por exemplo, os controles podem não aparecer na superfície de design.

## <a name="instances-of-this-error"></a>Instâncias desse erro

Quando a barra de erros amarela é expandida, cada instância do erro é listada. Muitos tipos de erro incluem um local exato no seguinte formato: *[nome do projeto]* *[nome do formulário]* linha: *[número da linha]* coluna: *[número da coluna]* . Se uma pilha de chamadas estiver associada ao erro, você poderá clicar no link **Mostrar pilha de chamadas** para vê-la. Examinar a pilha de chamadas pode ajudá-lo ainda mais a resolver o erro.

![Designer de Formulários do Windows erro expandido](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - Para Visual Basic aplicativos, a página de erro de tempo de design não exibe mais de um erro, mas pode exibir várias instâncias do mesmo erro.
> - Para C++ aplicativos, os erros não têm links de localização de código.

## <a name="help-with-this-error"></a>Ajuda com este erro

Se um tópico da ajuda para o erro estiver disponível, clique no link **ajuda do MSDN** para navegar diretamente para a página de ajuda no docs.Microsoft.com.

## <a name="forum-posts-about-this-error"></a>Postagens do fórum sobre este erro

Clique na **pesquisa nos fóruns do MSDN para postagens relacionadas a esse** link de erro para navegar até os fóruns do Microsoft Developer Network. Talvez você queira Pesquisar especificamente os fóruns de [Designer de formulários do Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) ou [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) .

## <a name="design-time-errors"></a>Erros de tempo de design

Esta seção lista alguns dos erros que você pode encontrar.

### <a name="identifier-name-is-not-a-valid-identifier"></a>' nome do identificador de\<> ' não é um identificador válido

Esse erro indica que um campo, método, evento ou objeto é nomeado incorretamente.

### <a name="name-already-exists-in-project-name"></a>'\<nome > ' já existe em '\<nome do projeto > '

Mensagem de erro: "'\<nome > ' já existe em '\<nome do projeto > '. Insira um nome exclusivo. "

Você especificou um nome para um formulário herdado que já existe no projeto. Para corrigir esse erro, dê ao formulário herdado um nome exclusivo.

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>'\<nome da guia caixa de ferramentas > ' não é uma categoria da caixa de ferramentas

Um designer de terceiros tentou acessar uma guia na caixa de ferramentas que não existe. Contate o fornecedor do componente.

### <a name="a-requested-language-parser-is-not-installed"></a>Um analisador de linguagem solicitado não está instalado

Mensagem de erro: "um analisador de idioma solicitado não está instalado. O nome do analisador de idioma é '{0}'. "

O Visual Studio tentou carregar um designer que está registrado para o tipo de arquivo, mas não pôde fazê-lo. Isso é provavelmente devido a um erro ocorrido durante a instalação. Entre em contato com o fornecedor do idioma que você está usando para uma correção.

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>Um serviço necessário para gerar e analisar o código fonte não foi encontrado

Esse é um problema com um componente de terceiros. Contate o fornecedor do componente.

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>Ocorreu uma exceção ao tentar criar uma instância de '\<o nome do objeto > '

Mensagem de erro: "ocorreu uma exceção ao tentar criar uma instância de '\<nome do objeto > '. A exceção foi "\<cadeia de caracteres de exceção\>".

Um designer de terceiros solicitou que o Visual Studio criasse um objeto, mas o objeto gerou um erro. Contate o fornecedor do componente.

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>Outro editor tem '\<nome do documento > ' aberto em um modo incompatível

Mensagem de erro: "outro editor tem '\<nome do documento > ' aberto em um modo incompatível. Feche o editor e tente esta operação novamente. "

Esse erro ocorrerá se você tentar abrir um arquivo que já está aberto em outro editor. O editor que já tem o arquivo aberto é mostrado. Para corrigir esse erro, feche o editor que tem o arquivo aberto e tente novamente.

### <a name="another-editor-has-made-changes-to-document-name"></a>Outro editor fez alterações no '\<nome do documento > '

Feche e reabra o designer para que as alterações entrem em vigor. Normalmente, o Visual Studio recarrega automaticamente um designer depois que as alterações são feitas. No entanto, outros designers, como designers de componentes de terceiros, podem não dar suporte ao comportamento de recarregamento. Nesse caso, o Visual Studio solicita que você feche e reabra o designer manualmente.

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>Outro editor tem o arquivo aberto em um modo incompatível

Mensagem de erro: "outro editor tem o arquivo aberto em um modo incompatível. Feche o editor e tente esta operação novamente. "

Essa mensagem é semelhante a "outro editor tem '\<nome do documento > ' aberto em um modo incompatível", mas o Visual Studio não pode determinar o nome do arquivo. Para corrigir esse erro, feche o editor que tem o arquivo aberto e tente novamente.

### <a name="array-rank-rank-in-array-is-too-high"></a>A classificação de matriz '\<classificação na matriz > ' é muito alta

O Visual Studio dá suporte apenas a matrizes de dimensão única no bloco de código que é analisado pelo designer. Matrizes multidimensionais são válidas fora desta área.

### <a name="assembly-assembly-name-could-not-be-opened"></a>Não foi possível abrir o assembly '\<nome do assembly > '

Mensagem de erro: "assembly"\<nome do assembly > ' não pôde ser aberto. Verifique se o arquivo ainda existe. "

Essa mensagem de erro surge quando você tenta abrir um arquivo que não pôde ser aberto. Verifique se o arquivo existe e se é um assembly válido.

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>Tipo de elemento inadequado. Este serializador espera um elemento do tipo '\<nome do tipo > '

Esse é um problema com um componente de terceiros. Contate o fornecedor do componente.

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>Não é possível acessar a caixa de ferramentas do Visual Studio neste momento

O Visual Studio fez uma chamada para a caixa de ferramentas, que não estava disponível. Se você vir esse erro, se você vir esse erro, registre um problema usando [relatar uma](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)questão.

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>Não é possível associar um manipulador de eventos ao evento '\<nome do evento > ' porque ele é somente leitura

Esse erro ocorre com mais frequência quando você tenta conectar um evento a um controle herdado de uma classe base. Se a variável de membro do controle for particular, o Visual Studio não poderá conectar o evento ao método. Controles herdados de forma privada não podem ter eventos adicionais associados a eles.

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>Não é possível criar um nome de método para o componente solicitado porque ele não é um membro do recipiente de design

O Visual Studio tentou adicionar um manipulador de eventos a um componente que não tem uma variável de membro no designer. Contate o fornecedor do componente.

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>Não é possível nomear o objeto '\<Name > ' porque ele já é denominado '\<Name > '

Este é um erro interno no serializador do Visual Studio. Isso indica que o serializador tentou nomear um objeto duas vezes, o que não tem suporte. Se você vir esse erro, registre um problema usando [relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>Não é possível remover ou destruir o componente herdado '\<nome do componente > '

Os controles herdados estão sob a propriedade de sua classe de herança. As alterações no controle herdado devem ser feitas na classe da qual o controle se origina. Portanto, você não pode renomeá-lo ou destruí-lo.

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>A categoria '\<nome da guia da caixa de ferramentas > ' não tem uma ferramenta para a classe '\<nome da classe > '

O designer tentou referenciar uma classe em uma guia de caixa de ferramentas específica, mas a classe não existe. Contate o fornecedor do componente.

### <a name="class-class-name-has-no-matching-constructor"></a>A classe '\<nome da classe > ' não tem um construtor correspondente

Um designer de terceiros solicitou que o Visual Studio criasse um objeto com parâmetros específicos no construtor que não existe. Contate o fornecedor do componente.

### <a name="code-generation-for-property-property-name-failed"></a>Falha na geração de código para a propriedade '\<nome da propriedade > '

Este é um wrapper genérico para um erro. A cadeia de caracteres de erro que acompanha essa mensagem fornecerá mais detalhes sobre a mensagem de erro e terá um link para um tópico de ajuda mais específico. Para corrigir esse erro, resolva o erro especificado na mensagem de erro anexada a esse erro.

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>O componente '\<nome do componente > ' não chamou o contêiner. Add () em seu construtor

Esse é um erro no componente que você acabou de carregar ou colocado no formulário. Ele indica que o componente não se adicionou a seu controle de contêiner (seja outro controle ou um formulário). O designer continuará a funcionar, mas pode haver problemas com o componente em tempo de execução.

Para corrigir o erro, contate o fornecedor do componente. Ou, se for um componente que você criou, chame o método `IContainer.Add` no construtor do componente.

### <a name="component-name-cannot-be-empty"></a>O nome do componente não pode ser deixado em branco

Esse erro ocorre quando você tenta renomear um componente para um valor vazio.

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>Não foi possível acessar a variável '\<nome da variável > ' porque ela ainda não foi inicializada

Esse erro pode ocorrer devido a dois cenários. Um fornecedor de componente de terceiros tem um problema com um controle ou componente que eles distribuiram ou o código que você escreveu tem dependências recursivas entre componentes.

Para corrigir esse erro, verifique se o seu código não tem uma dependência recursiva. Se ele estiver livre de tais problemas, observe o texto exato da mensagem de erro e contate o fornecedor do componente.

### <a name="could-not-find-type-type-name"></a>Não foi possível encontrar o tipo '\<nome do tipo > '

Mensagem de erro: "não foi possível encontrar o tipo '\<nome do tipo > '. Verifique se o assembly que contém esse tipo é referenciado. Se esse tipo fizer parte de seu projeto de desenvolvimento, certifique-se de que o projeto foi criado com êxito. "

Esse erro ocorreu porque uma referência não foi encontrada. Verifique se o tipo indicado na mensagem de erro é referenciado e se todos os assemblies que o tipo requer também são referenciados. Geralmente, o problema é que um controle na solução não foi criado. Para compilar, selecione **Compilar solução** no menu **Compilar** . Caso contrário, se o controle já tiver sido criado, adicione uma referência manualmente no menu do botão direito do mouse da pasta **References** ou **Dependencies** em Gerenciador de soluções.

### <a name="could-not-load-type-type-name"></a>Não foi possível carregar o tipo '\<nome do tipo > '

Mensagem de erro: "não foi possível carregar o tipo '\<nome do tipo > '. Certifique-se de que o assembly que contém esse tipo seja adicionado às referências do projeto. "

O Visual Studio tentou conectar um método de manipulação de eventos e não pôde localizar um ou mais tipos de parâmetro para o método. Isso geralmente é causado por uma referência ausente. Para corrigir esse erro, adicione a referência que contém o tipo ao projeto e tente novamente.

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>Não foi possível localizar os modelos de itens do projeto para componentes herdados

Os modelos para formulários herdados no Visual Studio não estão disponíveis. Se você vir esse erro, registre um problema usando [relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>A classe delegada '\<nome da classe > ' não tem um método Invoke. Essa classe é um delegado?

O Visual Studio tentou criar um manipulador de eventos, mas há algo errado com o tipo de evento. Isso pode acontecer se o evento foi criado por uma linguagem não compatível com CLS. Contate o fornecedor do componente.

### <a name="duplicate-declaration-of-member-member-name"></a>Declaração duplicada do membro '\<nome do membro > '

Esse erro ocorre porque uma variável de membro foi declarada duas vezes (por exemplo, dois controles chamados `Button1` são declarados no código). Os nomes devem ser exclusivos em formulários herdados. Além disso, nomes não podem diferir apenas por maiúsculas e minúsculas.

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>Erro ao ler os recursos do arquivo de recursos para a cultura '\<nome de cultura > '

Esse erro pode ocorrer se houver um arquivo. resx inadequado no projeto.

Para corrigir esse erro:

1. Clique no botão **Mostrar todos os arquivos** em Gerenciador de soluções para exibir os arquivos. resx associados à solução.
2. Carregue o arquivo. resx no editor de XML clicando com o botão direito do mouse no arquivo. resx e escolhendo **abrir**.
3. Edite o arquivo. resx manualmente para resolver os erros.

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>Erro ao ler os recursos do arquivo de recursos para a cultura padrão '\<nome da cultura > '

Esse erro pode ocorrer se houver um arquivo. resx inadequado no projeto para a cultura padrão.

Para corrigir esse erro:

1. Clique no botão **Mostrar todos os arquivos** em Gerenciador de soluções para exibir os arquivos. resx associados à solução.
2. Carregue o arquivo. resx no editor de XML clicando com o botão direito do mouse no arquivo. resx e escolhendo **abrir**.
3. Edite o arquivo. resx manualmente para resolver os erros.

### <a name="failed-to-parse-method-method-name"></a>Falha ao analisar o método '\<nome do método > '

Mensagem de erro: "falha ao analisar o método '\<nome do método > '. O analisador relatou o seguinte erro: '\<cadeia de caracteres de erro > '. Consulte a Lista de Tarefas para obter possíveis erros ".

Essa é uma mensagem de erro geral para problemas que surgem durante a análise. Esses erros costumam ocorrer devido a erros de sintaxe. Consulte a Lista de Tarefas para mensagens específicas relacionadas ao erro.

### <a name="invalid-component-name-component-name"></a>Nome de componente inválido: '\<nome do componente > '

Você tentou renomear um componente para um valor inválido para esse idioma. Para corrigir esse erro, nomeie o componente de modo que ele esteja em conformidade com as regras de nomenclatura para esse idioma.

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>O tipo '\<nome da classe > ' é composto por várias classes parciais no mesmo arquivo

Quando você define uma classe em vários arquivos usando a palavra-chave [partial](../../../csharp/language-reference/keywords/partial-type.md) , só pode ter uma definição parcial em cada arquivo.

Para corrigir esse erro, remova todas, exceto uma das definições parciais da sua classe, do arquivo.

### <a name="the-assembly-assembly-name-could-not-be-found"></a>Não foi possível encontrar o assembly '\<nome do assembly > '

Mensagem de erro: "o assembly '\<nome do assembly > ' não foi encontrado. Verifique se o assembly é referenciado. Se o assembly fizer parte do projeto de desenvolvimento atual, verifique se o projeto foi criado. "

Esse erro é semelhante a "o tipo\<nome > ' não pôde ser encontrado", mas esse erro geralmente ocorre devido a um atributo de metadados. Para corrigir esse erro, verifique se todos os assemblies usados por atributos são referenciados.

### <a name="the-assembly-name-assembly-name-is-invalid"></a>O nome do assembly '\<Assembly Name > ' é inválido

Um componente solicitou um assembly específico, mas o nome fornecido pelo componente não é um nome de assembly válido. Contate o fornecedor do componente.

### <a name="the-base-class-class-name-cannot-be-designed"></a>A classe base '\<nome da classe > ' não pode ser projetada

O Visual Studio carregou a classe, mas a classe não pode ser projetada porque o implementador da classe não forneceu um designer. Se a classe oferecer suporte a um designer, certifique-se de que não haja nenhum problema que cause problemas ao exibi-lo em um designer, como erros do compilador. Além disso, verifique se todas as referências à classe estão corretas e se todos os nomes de classe estão escritos corretamente. Caso contrário, se a classe não for designável, edite-a no modo de exibição de código.

### <a name="the-base-class-class-name-could-not-be-loaded"></a>A classe base '\<nome da classe > ' não pôde ser carregada

A classe não é referenciada no projeto, portanto o Visual Studio não pode carregá-la. Para corrigir esse erro, adicione uma referência à classe no projeto e feche e reabra a janela de Designer de Formulários do Windows.

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>A classe '\<nome da classe > ' não pode ser projetada nesta versão do Visual Studio

O designer deste controle ou componente não oferece suporte aos mesmos tipos que o Visual Studio faz. Contate o fornecedor do componente.

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>O nome da classe não é um identificador válido para este idioma

O código-fonte que está sendo criado pelo usuário tem um nome de classe que não é válido para o idioma que está sendo usado. Para corrigir esse erro, nomeie a classe de forma que ela esteja de acordo com os requisitos de idioma.

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>O componente não pode ser adicionado porque contém uma referência circular para '\<nome de referência > '

Você não pode adicionar um controle ou componente a si mesmo. Outra situação em que isso pode ocorrer é o código no método InitializeComponent de um formulário (por exemplo, Form1) que cria outra instância do Form1.

### <a name="the-designer-cannot-be-modified-at-this-time"></a>O designer não pode ser modificado no momento

Esse erro ocorre quando o arquivo no editor é marcado como somente leitura. Verifique se o arquivo não está marcado como somente leitura e se o aplicativo não está em execução.

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>O designer não pôde ser mostrado para esse arquivo porque nenhuma das classes existentes nele podem ser criadas

Esse erro ocorre quando o Visual Studio não pode encontrar uma classe base que atenda aos requisitos do designer. Formulários e controles devem derivar de uma classe base que ofereça suporte a designers. Se você estiver derivando de um formulário ou controle herdado, verifique se o projeto foi compilado.

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>O designer da classe base '\<nome da classe > ' não está instalado

O Visual Studio não pôde carregar o designer para a classe. Se você vir esse erro, registre um problema usando [relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>O designer deve criar uma instância do tipo '\<nome do tipo > ', mas não pode porque o tipo é declarado como abstrato

Esse erro ocorreu porque a classe base do objeto que está sendo passado para o designer é [abstrata](../../../csharp/language-reference/keywords/abstract.md), o que não é permitido.

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>Não foi possível carregar o arquivo no designer

A classe base deste arquivo não oferece suporte a designers. Como alternativa, use a exibição de código para trabalhar no arquivo. Clique com o botão direito do mouse no arquivo em Gerenciador de Soluções e escolha **Exibir código**.

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>A linguagem deste arquivo não suporta a análise de código e geração de serviços necessários

Mensagem de erro: "o idioma deste arquivo não dá suporte aos serviços de análise e geração de código necessários. Verifique se o arquivo que você está abrindo é membro de um projeto e tente abri-lo novamente. "

Esse erro provavelmente resultou na abertura de um arquivo que está em um projeto que não oferece suporte a designers.

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>A classe do analisador de linguagem '\<nome da classe > ' não está implementada corretamente

Mensagem de erro: "a classe do analisador de linguagem '\<nome da classe > ' não está implementada corretamente. Contate o fornecedor para obter um módulo Analisador atualizado. "

O idioma em uso registrou uma classe de designer que não deriva da classe base correta. Contate o fornecedor do idioma que você está usando.

### <a name="the-name-name-is-already-used-by-another-object"></a>O nome '\<nome > ' já está sendo usado por outro objeto

Este é um erro interno no serializador do Visual Studio. Se você vir esse erro, registre um problema usando [relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>O objeto '\<nome do objeto > ' não implementa a interface IComponent

O Visual Studio tentou criar um componente, mas o objeto criado não implementa a interface <xref:System.ComponentModel.IComponent>. Contate o fornecedor do componente para obter uma correção.

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>O objeto '\<nome do objeto > ' retornou nulo para a propriedade '\<nome da propriedade > ', mas isso não é permitido

Há algumas propriedades do .NET que sempre devem retornar um objeto. Por exemplo, a coleção **Controls** de um formulário sempre deve retornar um objeto, mesmo quando não há controles nele.

Para corrigir esse erro, verifique se a propriedade especificada no erro não é nula.

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>O objeto de dados de serialização não é do tipo adequado

Um objeto de dados oferecido pelo serializador não é uma instância de um tipo que corresponda ao serializador atual que está sendo usado. Contate o fornecedor do componente.

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>O serviço '\<nome do serviço > ' é necessário, mas não foi localizado

Mensagem de erro: "o nome do serviço de\<do serviço ' > ' é necessário, mas não foi localizado. Pode haver um problema com a instalação do Visual Studio. "

Um serviço exigido pelo Visual Studio não está disponível. Se você estiver tentando carregar um projeto que não oferece suporte a esse designer, use o editor de código para fazer as alterações necessárias. Caso contrário, se você vir esse erro, registre um problema usando [relatar um problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>A instância de serviço deve derivar ou implementar '\<nome da interface > '

Esse erro indica que um componente ou designer de componente chamou o método **AddService** , que requer uma interface e um objeto, mas o objeto especificado não implementa a interface especificada. Contate o fornecedor do componente.

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>Não foi possível modificar o texto na janela de código

Mensagem de erro: "não foi possível modificar o texto na janela de código. Verifique se o arquivo não é somente leitura e se há espaço em disco suficiente. "

Esse erro ocorre quando o Visual Studio não pode editar um arquivo devido a problemas de memória ou espaço em disco, ou o arquivo está marcado como somente leitura.

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>O objeto enumerados da caixa de ferramentas só dá suporte para recuperar um item de cada vez

Se você vir esse erro, se você vir esse erro, registre um problema usando [relatar uma](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)questão.

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>O item da caixa de ferramentas para '\<nome do componente > ' não pôde ser recuperado da caixa de ferramentas

Mensagem de erro: "o item da caixa de ferramentas para '\<nome do componente > ' não pôde ser recuperado da caixa de ferramentas. Verifique se o assembly que contém o item da caixa de ferramentas está instalado corretamente. O item da caixa de ferramentas gerou o seguinte erro: \<cadeia de caracteres de erro >. "

O componente em questão emitiu uma exceção quando o Visual Studio o acessou. Contate o fornecedor do componente.

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>O item da caixa de ferramentas para '\<nome do item da caixa de ferramentas > ' não pôde ser recuperado da caixa de ferramentas

Mensagem de erro: "o item da caixa de ferramentas para '\<nome do item da caixa de ferramentas > ' não pôde ser recuperado da caixa de ferramentas. Tente remover o item da caixa de ferramentas e adicioná-lo de volta. "

Esse erro ocorrerá se os dados no item da caixa de ferramentas forem corrompidos ou se a versão do componente tiver sido alterada. Tente remover o item da caixa de ferramentas e adicioná-lo novamente.

### <a name="the-type-type-name-could-not-be-found"></a>O tipo '\<nome do tipo > ' não pôde ser encontrado

Mensagem de erro: "o tipo '\<nome do tipo > ' não foi encontrado. Verifique se o assembly que contém o tipo é referenciado. Se o assembly fizer parte do projeto de desenvolvimento atual, verifique se o projeto foi criado. "

Ao carregar o designer, o Visual Studio não conseguiu encontrar um tipo. Verifique se o assembly que contém o tipo é referenciado. Se o assembly fizer parte do projeto de desenvolvimento atual, verifique se o projeto foi compilado.

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>O serviço de digitação com resolução só pode ser chamado pelo segmento do aplicativo principal

O Visual Studio tentou acessar os recursos necessários do thread incorreto. Esse erro é exibido quando o código usado para criar o designer chamou o serviço de resolução de tipo de um thread que não seja o thread do aplicativo principal. Para corrigir esse erro, chame o serviço do thread correto ou contate o fornecedor do componente.

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>A variável '\<nome da variável > ' está não declarada ou nunca foi atribuída

O código-fonte tem uma referência a uma variável, como **Button1**, que não é declarada ou atribuída. Se a variável não tiver sido atribuída, essa mensagem aparecerá como um aviso, não um erro.

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>Já existe um manipulador de comandos para o comando de menu '\<nome do comando de menu > '

Esse erro ocorrerá se um designer de terceiros adicionar um comando que já tem um manipulador para a tabela de comandos. Contate o fornecedor do componente.

### <a name="there-is-already-a-component-named-component-name"></a>Já existe um componente chamado ' nome do componente de\<> '

Mensagem de erro: "já existe um componente chamado '\<nome do componente > '. Os componentes devem ter nomes exclusivos, e os nomes não devem diferenciar maiúsculas de minúsculas. Um nome também não pode entrar em conflito com o nome de qualquer componente em uma classe herdada. "

Essa mensagem de erro surge quando houve uma alteração no nome de um componente no janela Propriedades. Para corrigir esse erro, certifique-se de que todos os nomes de componentes sejam exclusivos, não diferenciam maiúsculas de minúsculas e não entrem em conflito com os nomes de quaisquer componentes nas classes herdadas.

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>Já existe um criador de item de caixa de ferramentas registrado para o formato '\<nome do formato > '

Um componente de terceiros fez um retorno de chamada para um item em uma guia da caixa de ferramentas, mas o item já continha um retorno de chamada. Contate o fornecedor do componente.

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>Este mecanismo de idioma não suporta um CodeModel com o qual carregar um designer

Esta mensagem é semelhante a "o idioma deste arquivo não dá suporte aos serviços de geração e análise de código necessários", mas essa mensagem envolve um problema de registro interno. Se você vir esse erro, se você vir esse erro, registre um problema usando [relatar uma](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)questão.

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>O tipo '\<nome do tipo\>' não tem um construtor com parâmetros dos tipos '\<nomes de tipo de parâmetro > '

O Visual Studio não pôde encontrar um [Construtor](../../../csharp/programming-guide/classes-and-structs/constructors.md) que tinha parâmetros correspondentes. Isso pode ser o resultado do fornecimento de um construtor com tipos diferentes daqueles necessários. Por exemplo, um construtor de **pontos** pode levar dois inteiros. Se você tiver fornecido floats, esse erro será gerado.

Para corrigir esse erro, use um Construtor diferente ou converta explicitamente os tipos de parâmetro de forma que eles correspondam àqueles fornecidos pelo construtor.

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>Não é possível adicionar a referência '\<nome de referência > ' ao aplicativo atual

Mensagem de erro: "não é possível adicionar a referência '\<nome de referência > ' ao aplicativo atual. Verifique se uma versão diferente do '\<nome de referência > ' já não está referenciada. "

O Visual Studio não pode adicionar uma referência. Para corrigir esse erro, verifique se uma versão diferente da referência ainda não está referenciada.

### <a name="unable-to-check-out-the-current-file"></a>Não é possível fazer check-out do arquivo atual

Mensagem de erro: "não é possível fazer check-out do arquivo atual. O arquivo pode estar bloqueado ou você pode precisar fazer check-out do arquivo manualmente. "

Esse erro ocorre quando você altera um arquivo que está selecionado no momento para o controle do código-fonte. Normalmente, o Visual Studio apresenta a caixa de diálogo check-out do arquivo para que o usuário possa fazer check-out do arquivo. Desta vez, o arquivo não foi extraído, talvez devido a um conflito de mesclagem durante o check-out. Para corrigir esse erro, verifique se o arquivo não está bloqueado e tente fazer check-out do arquivo manualmente.

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>Não é possível localizar a página denominada ' opções de\<nome da guia da caixa de diálogo > '

Esse erro ocorre quando um designer de componentes solicita acesso a uma página da caixa de diálogo opções usando um nome que não existe. Contate o fornecedor do componente.

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>Não é possível localizar a propriedade '\<nome da propriedade > ' na página '\<nome da guia da caixa de diálogo Opções > '

Esse erro ocorre quando um designer de componentes solicita acesso a um valor específico em uma página da caixa de diálogo opções, mas esse valor não existe. Contate o fornecedor do componente.

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>O Visual Studio não pode abrir um designer para o arquivo porque a classe nele não herda de uma classe que pode ser projetada visualmente

O Visual Studio carregou a classe, mas o designer dessa classe não pôde ser carregado. O Visual Studio requer que os designers usem a primeira classe em um arquivo. Para corrigir esse erro, mova o código de classe para que ele seja a primeira classe no arquivo e, em seguida, carregue o designer novamente.

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>O Visual Studio não pode salvar ou carregar instâncias do tipo '\<nome do tipo > '

Esse é um problema com um componente de terceiros. Contate o fornecedor do componente.

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>O Visual Studio não pode abrir '\<nome do documento > ' em modo de exibição de Design

Mensagem de erro: "o Visual Studio não pode abrir '\<nome do documento > ' em modo de exibição de Design. Nenhum analisador está instalado para o tipo de arquivo. "

Esse erro indica que o idioma do projeto não oferece suporte a um designer e surge quando você tenta abrir um arquivo na caixa de diálogo abrir arquivo ou de Gerenciador de Soluções. Em vez disso, edite o arquivo no modo de exibição de código.

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>O Visual Studio não conseguiu encontrar um designer para classes do tipo '\<nome do tipo > '

O Visual Studio carregou a classe, mas a classe não pode ser projetada. Em vez disso, edite a classe na exibição de código clicando com o botão direito do mouse na classe e escolhendo **Exibir código**.

## <a name="see-also"></a>Consulte também

- [Desenvolver Windows Forms controles usando o designer](developing-windows-forms-controls-at-design-time.md)
- [Fórum de Designer de Formulários do Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
