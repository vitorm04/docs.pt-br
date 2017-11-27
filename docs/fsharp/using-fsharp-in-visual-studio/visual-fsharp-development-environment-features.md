---
title: Funcionalidades do ambiente de desenvolvimento em F#
description: "Saiba quais recursos do Visual Studio 2012 têm suporte em F #."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 809e9a34-b271-4c87-8356-2426b44f4721
ms.openlocfilehash: bcba1e5d1cae1c610525c51bdbdd54088359e79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-f-development-environment-features"></a>Recursos do Ambiente de Desenvolvimento em Visual F#

> [!NOTE]
Este artigo não é atualizado com o mais recente do Visual Studio.  Ele será atualizado.

Este tópico inclui informações sobre quais recursos do Visual Studio 2012 têm suporte em F #.

## <a name="project-features"></a>Recursos de projeto
A tabela a seguir resume os modelos que estão disponíveis para uso em projetos F #. Para obter informações sobre modelos de projeto e item, consulte [NIB criar projetos de modelos](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2).

|Tipo de modelo|Descrição|Modelos com suporte|
|-------------|-----------|-------------------|
|Modelos de projeto|Tipos de projetos disponíveis no **novo projeto** caixa de diálogo.|<ul><li>Aplicativo de F #<br /></li><li>Biblioteca F #<br /></li><li>F # Tutorial<br /></li><li>Biblioteca do F # portátil<br /></li><ul/>|
|Modelos de item|Tipos disponíveis em arquivos de **Adicionar Novo Item** caixa de diálogo.|<ul><li>Arquivo de origem F # (. FS)<br /></li><li>F # script (. fsx)<br /></li><li>Arquivo de assinatura de F # (. FSI)<br /></li><li>Arquivo de configuração (. config)<br /></li><li>Conexão de banco de dados SQL (provedor de tipos do LINQ to SQL)<br /></li><li>Conexão de banco de dados SQL (provedor LINQ to Entities tipo)<br /></li><li>Conexão de serviço OData (provedor de tipo LINQ)<br /></li><li>Conexão de serviço WSDL (provedor de tipo)<br /></li><li>Arquivo XML (. xml)<br /></li><li>Arquivo de texto<br /></li><ul/>|
Para criar um aplicativo que pode ser executado como um executável autônomo, escolha o tipo de projeto de aplicativo do F #. Para criar uma biblioteca (ou seja, um assembly gerenciado ou. Arquivo DLL) para uso na plataforma de área de trabalho do Windows, escolha biblioteca F #. Para criar uma biblioteca portátil que pode ser usada em qualquer plataforma com suporte, escolha biblioteca F # portátil. Projetos de biblioteca F # portátil referenciam uma versão do FSharp.Core.dll é apropriada para criar uma biblioteca F # que pode ser usada com aplicativos que são executados em plataformas, como aplicativos da Windows Store, o .NET Framework 4.5, xamarin e xamarin.

Para obter mais informações sobre os modelos de item para acesso a dados, consulte [provedores de tipos](../tutorials/type-providers/index.md).

A tabela a seguir resume os recursos de propriedades do projeto ou não suporte em F #. Para obter mais informações, consulte [Configurando projetos](configuring-projects.md) e [Introdução ao Project Designer](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7).

|Configuração de projeto|Com suporte em F #?|Observações|
|---------------|----------------|-----|
|Arquivos de recurso|Sim||
|Compilação, depuração e configurações de referência|Sim||
|Multiplataforma|Sim||
|Ícone e manifesto|Não|Disponível por meio das opções de linha de comando do compilador.|
|Serviços de cliente do ASP.NET|Não||
|ClickOnce|Não|Use um projeto de cliente em outra linguagem do .NET Framework, se aplicável.|
|Nomenclatura forte|Não|Disponível por meio das opções de linha de comando do compilador.|
|Assembly de publicação e controle de versão|Não||
|Análise de código|Não|Ferramentas de análise de código podem ser executadas manualmente ou como parte de um comando de pós-compilação.|
|Segurança (níveis de confiança de alteração)|Não||

## <a name="code-and-text-editor-features"></a>Recursos do Editor de texto e código
Os seguintes recursos do Visual Studiocode e editores de texto têm suporte em F #. Para obter informações gerais sobre a edição de código no Visual Studio e recursos do editor de texto, consulte [escrevendo código no Editor de texto de código e](https://msdn.microsoft.com/library/efc4xwkb.aspx).

|Recurso|Descrição|Com suporte em F #?|
|-------|-----------|----------------|
|Comentário automaticamente|Permite que você comente ou remova os comentários de seções de código.|Sim|
|Formatar automaticamente|Reformata o código com recuo padrão e estilo.|Não|
|Indicadores|Permite que você salve locais no editor.|Sim|
|Alterar o recuo|Recua ou unindents linhas selecionadas.|Sim|
|[Localizando e substituindo texto](https://msdn.microsoft.com/library/139eef4h.aspx)|Permite pesquisar em um arquivo, projeto ou solução e potencialmente altere o texto.|Sim|
|Ir para definição de API do .NET Framework|Quando o cursor estiver posicionado em uma API do .NET Framework, mostra o código gerado a partir de metadados do .NET Framework.|Não|
|Ir para definição de API definida pelo usuário|Quando o cursor estiver em uma entidade de programa que você definiu, move o cursor para o local em seu código onde a entidade é definida.|Sim|
|Ir para a linha|Permite que você acesse uma linha específica em um arquivo, por número de linha.|Sim|
|Barras de navegação na parte superior do arquivo|Habilita a saltar para locais no código, por, por exemplo, o nome da função.|Sim|
|Estrutura. Consulte [de estrutura de tópicos](https://msdn.microsoft.com/library/td6a5x4s.aspx).|Permite que você recolher seções do seu código para criar uma exibição mais compacta.|Sim|
|Tabular|Converte espaços em tabulações.|Sim|
|Colorização de tipo|Mostra definidos nomes de tipo em uma cor especial.|Sim|
|Localização rápida. Consulte localização rápida, localizar e substituir a janela.|Permite pesquisar em um arquivo ou projeto.|Sim|

## <a name="intellisense-features"></a>Recursos do IntelliSense
A tabela a seguir resume os recursos do IntelliSense, suporte e não tem suporte em F #. Para obter informações gerais sobre o IntelliSense, consulte [usando o IntelliSense](https://msdn.microsoft.com/library/hcw1s69b.aspx).

|Recurso|Descrição|Com suporte em F #?|
|-------|-----------|----------------|
|Implementar automaticamente as interfaces|Gera stubs de código para métodos de interface.|Não|
|Trechos de código|Insere um código de uma biblioteca de construções de codificação comuns em tópicos.|Não|
|Completar Palavra|Salva digitando completando palavras e os nomes conforme você digita.|Sim|
|Modo de conclusão da primeira consumir|Quando habilitado, faz com que a conclusão do word selecionar a primeira correspondência que você digita, em vez de esperar para que você selecione um ou pressione **CTRL + espaço**.|Não|
|Gerar elementos de código|Permite que você gerar o código de stub de uma variedade de construções.|Não|
|Listar Membros|Quando você digita o operador de acesso de membro (.), mostra os membros de um tipo.|Sim|
|Organizar usos/abrir|Organiza os namespaces referenciados por **usando** instruções em c# ou **abrir** diretivas em F #.|Não|
|Informações de Parâmetro|Mostra informações úteis sobre parâmetros conforme você digita uma chamada de função.|Sim|
|Informação Rápida|Exibe a declaração completa de qualquer identificador em seu código.|Sim|
Refatoração do código F # não tem suporte no Visual Studio 2012.

## <a name="debugging-features"></a>Recursos de depuração
A tabela a seguir resume os recursos que estão disponíveis quando você depura o código F #. Para obter informações gerais sobre o depurador do Visual Studio, consulte [depuração no Visual Studio](https://msdn.microsoft.com/library/sc65sadd.aspx).

|Recurso|Descrição|Com suporte em F #?|
|-------|-----------|----------------|
|Janela Autos|Mostra as variáveis automáticas ou temporárias.|Não|
|Pontos de interrupção|Permite que você pause a execução de código em pontos específicos durante a depuração.|Sim|
|Pontos de interrupção condicionais|Permite que os pontos de interrupção que uma condição que determina se deve pausar a execução de teste.|Sim|
|Editar e continuar|Permite que o código a ser modificada e compilados como depurar um programa em execução sem interromper e reiniciar o depurador.|Não|
|Avaliador de expressão|Avalia e executa código em tempo de execução.|Não, mas o c# avaliador de expressão pode ser usado, embora você deve usar a sintaxe do c#.|
|Depuração histórica|Permite que você entrar no código executado anteriormente.|Sim|
|Janela Locais|Mostra localmente definidos valores e variáveis.|Sim|
|Executar até o cursor|Permite que você execute o código até que a linha que contém o cursor for atingida.|Sim|
|Entrar em|Permite que você adiantar a execução e mover para qualquer chamada de função.|Sim|
|Depuração Parcial|Permite que você adiantar a execução no quadro de pilhas atual e passa a qualquer chamada de função.|Sim|

## <a name="additional-tools"></a>Ferramentas adicionais
A tabela a seguir resume o suporte para F # em ferramentas do Visual Studio.

|Ferramenta|Descrição|Com suporte em F #?|
|----|-----------|----------------|
|Hierarquia de chamadas|Exibe a estrutura aninhada de função chama em seu código.|Não|
|Métricas de código|Reúne informações sobre seu código, como contagens de linha.|Não|
|Exibição de Classe|Fornece uma exibição baseada no tipo de código em um projeto.|Não|
|[Janela Lista de Erros](https://msdn.microsoft.com/library/33df3b7a.aspx)|Mostra uma lista de erros no código.|Sim|
|[F# Interativo](../tutorials/fsharp-interactive/index.md)|Permite digitar (ou copie e cole) F # de código e executá-lo imediatamente, independentemente da criação do projeto. A janela F # interativo é uma leitura, avaliar, impressão Loop REPL ().|Sim|
|Pesquisador de Objetos|Permite que você veja os tipos em um assembly.|Tipos F # que aparecem em módulos compilados não aparecer exatamente como você criá-los. Você pode examinar a representação compilada de tipos F #, mas não é possível exibir os tipos conforme elas aparecem de F #.|
|[Janela de Saída](https://msdn.microsoft.com/library/3hk6fby3.aspx)|Exibe a saída de compilação.|Sim|
|Análise de desempenho|Fornece ferramentas para medir o desempenho do seu código.|Sim|
|Janela Propriedades|Exibe e permite a edição das propriedades do objeto no ambiente de desenvolvimento que tem o foco.|Sim|
|[Gerenciador de servidores](https://msdn.microsoft.com/library/x603htbk.aspx)|Fornece formas de interagir com uma variedade de recursos de servidor.|Sim|
|Gerenciador de Soluções|Permite exibir e gerenciar projetos e arquivos.|Sim|
|Lista de Tarefas|Permite que você gerencie os itens de trabalho pertencentes ao seu código.|Sim|
|Projetos de teste|Fornece recursos que ajudam você a testar seu código.|Não|
|Caixa de Ferramentas|Exibe as guias que contêm objetos arrastáveis, como controles e seções de texto ou código.|Sim|

## <a name="see-also"></a>Consulte também
 [Introdução à linguagem F # no Visual Studio](../get-started/get-started-visual-studio.md)  
 [Configurando Projetos](configuring-projects.md)  
