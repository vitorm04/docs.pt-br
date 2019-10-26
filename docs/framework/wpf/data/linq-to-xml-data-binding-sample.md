---
title: Exemplo de associação de dados LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920933"
---
# <a name="linq-to-xml-data-binding-sample"></a>Exemplo de associação de dados LINQ to XML

Este artigo descreve o exemplo LinqToXmlDataBinding, um aplicativo Windows Presentation Foundation (WPF) que associa os componentes da interface do usuário a uma fonte de dados XML inserida.

## <a name="overview"></a>Visão Geral

O exemplo LinqToXmlDataBinding é um aplicativo Windows Presentation Foundation (WPF) que contém C# e arquivos de origem XAML. Um documento XML inserido define uma lista de livros. O aplicativo permite que o usuário exiba, adicione, exclua e edite as entradas do livro.

Há dois arquivos de origem principais:

- [L2DBForm.xaml](l2dbform-xaml-source-code.md) contém o código de declaração XAML para a interface do usuário da janela principal. Ele também contém uma seção de recursos de janela que define um provedor de dados e um documento XML inserido para as listagens de livros.

- [L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contém os métodos de inicialização e de manipulação de eventos associados à interface do usuário.

A janela principal é dividida nas quatro seções verticais de interface de usuário:

- **XML** exibe o código-fonte XML bruto da listagem de livros inserida.

- **Lista de livros** exibe as entradas de livro como texto padrão e permite que o usuário selecione e exclua entradas individuais.

- **Editar Livro Selecionado** permite que o usuário edite os valores associados à entrada do livro selecionada no momento.

- **Adicionar Novo Livro** habilita a criação de uma nova entrada de livro com base nos valores inseridos pelo usuário.

## <a name="run-the-sample"></a>Executar o exemplo

Esta seção mostra como criar e compilar o projeto LinqToXmlDataBinding no Visual Studio e como executar o aplicativo LinqToXmlDataBinding Windows Presentation Foundation (WPF) resultante.

### <a name="create-the-project"></a>Criar o projeto

1. Inicie o Visual Studio e crie um **WPF App** em C# chamado **LinqToXmlDataBinding**.

   O projeto deve direcionar o .NET Framework 3.5 (ou posterior).

1. Se ainda não presentes, adicione referências de projeto para os seguintes conjuntos de módulos (assemblies) .NET:

    - System.Data
    - System.Data.DataSetExtensions
    - System.Xml
    - System.Xml

1. Crie a solução pressionando **Ctrl**+**Shift**+**B** e execute-a pressionando **F5**.

   O projeto deve compilar sem erros e como executar um aplicativo genérica de WPF.

### <a name="add-code"></a>Adicionar código

1. No **Gerenciador de Soluções**, renomeie o arquivo de origem **Window1.xaml** como **L2XDBForm.xaml**.

   O arquivo de origem dependente Window1.xaml.cs é automaticamente renomeado para L2XDBForm.xaml.cs.

1. Substitua o código-fonte encontrado no arquivo **L2XDBForm. XAML** pelo [código-fonte L2DBForm. XAML](l2dbform-xaml-source-code.md). Use o modo de exibição XAML para trabalhar com esse arquivo.

1. Da mesma forma, substitua a origem em **L2XDBForm.XAML.cs** pelo [código-fonte L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).

1. No arquivo **app. XAML**, substitua todas as ocorrências da cadeia de caracteres **Window1. XAML** por **L2XDBForm. XAML**.

1. Crie a solução pressionando **Ctrl**+**Shift**+**B**.

### <a name="run-the-app"></a>Executar o aplicativo

O aplicativo LinqToXmlDataBinding permite que o usuário exiba e manipule uma lista de livros que é armazenada como um elemento XML inserido. Execute o aplicativo pressionando **F5** (Iniciar Depuração) ou **Ctrl**+**F5** (Iniciar sem depuração).

É exibida uma janela de programa com o título **Associação de dados do WPF usando LINQ to XML**.

A seção superior da interface do usuário exibe o **XML** bruto que representa a lista de livros. É exibida usando um controle de <xref:System.Windows.Controls.TextBlock> WPF, que não permite a interação por meio do mouse ou do teclado.

A segunda seção vertical, rotulada como **Lista de livros**, exibe os livros como uma lista ordenada de texto sem formatação. Usa um controle de <xref:System.Windows.Controls.ListBox> que permite a seleção embora o mouse ou o teclado.

### <a name="add-and-delete-books"></a>Adicionar e excluir livros

Para adicionar um novo livro à lista, insira valores na **ID** e no **valor** <xref:System.Windows.Controls.TextBox> controles na última seção, **Adicionar novo livro**e, em seguida, selecione **Adicionar livro**. O livro é acrescentado à lista no livro e nas listagens XML. Este programa não validar valores de entrada.

Para excluir um livro existente da lista, selecione-o na seção **lista de livros** e, em seguida, selecione **remover livro selecionado**. A entrada do livro é removida do livro e das listagens de origem XML brutas.

### <a name="edit-a-book-entry"></a>Editar uma entrada de livro

1. Selecione a entrada de livro na segunda seção da **Lista de livros**.

   Seus valores atuais são exibidos na seção **Editar livro selecionado** .

1. Editar os valores usando o teclado. Assim que o controle de <xref:System.Windows.Controls.TextBox> perde o foco, as alterações são automaticamente propagadas para a origem XML e listagens de livros.
