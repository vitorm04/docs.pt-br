---
title: Como criar exceções definidas pelo usuário com mensagens de exceção localizadas
description: Saiba como criar exceções definidas pelo usuário com mensagens de exceção localizadas
author: Youssef1313
dev_langs:
- csharp
- vb
ms.date: 09/13/2019
ms.openlocfilehash: 5a02c71b16e2c8e5ade5128866af7dc46a03ba4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160177"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Como criar exceções definidas pelo usuário com mensagens de exceção localizadas

Neste artigo, você aprenderá a criar exceções definidas pelo <xref:System.Exception> usuário que são herdadas da classe base com mensagens de exceção localizadas usando conjuntos de satélites.

## <a name="create-custom-exceptions"></a>Criar exceções personalizadas

.NET contém muitas exceções diferentes que você pode usar. No entanto, em alguns casos, quando nenhum deles atende às suas necessidades, você pode criar suas próprias exceções personalizadas.

Vamos supor que você `StudentNotFoundException` queira `StudentName` criar um que contenha uma propriedade.
Para criar uma exceção personalizada, siga estas etapas:

1. Crie uma classe serializável <xref:System.Exception>que herde de . O nome da classe deve terminar em "Exceção":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception
    End Class
    ```

1. Adicionar os construtores padrão:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub
    End Class
    ```

1. Defina quaisquer propriedades e construtores adicionais:

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

    ```vb
    <Serializable>
    Public Class StudentNotFoundException
        Inherits Exception

        Public ReadOnly Property StudentName As String

        Public Sub New()
        End Sub

        Public Sub New(message As String)
            MyBase.New(message)
        End Sub

        Public Sub New(message As String, inner As Exception)
            MyBase.New(message, inner)
        End Sub

        Public Sub New(message As String, studentName As String)
            Me.New(message)
            StudentName = studentName
        End Sub
    End Class
    ```

## <a name="create-localized-exception-messages"></a>Criar mensagens de exceção localizadas

Você criou uma exceção personalizada, e você pode jogá-la em qualquer lugar com código como o seguinte:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

```vb
Throw New StudentNotFoundException("The student cannot be found.", "John")
```

O problema com a `"The student cannot be found."` linha anterior é que é apenas uma seqüência constante. Em um aplicativo localizado, você deseja ter mensagens diferentes dependendo da cultura do usuário.
[Conjuntos de satélites](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) são uma boa maneira de fazer isso. Uma montagem via satélite é uma .dll que contém recursos para uma língua específica. Quando você pede recursos específicos no tempo de execução, o CLR encontra esse recurso dependendo da cultura do usuário. Se não for encontrado nenhum conjunto de satélite para essa cultura, os recursos da cultura padrão serão usados.

Para criar as mensagens de exceção localizadas:

1. Crie uma nova pasta chamada *Resources* para manter os arquivos de recursos.
1. Adicione um novo arquivo de recursos a ele. Para fazer isso no Visual Studio, clique com o botão direito do mouse na pasta no **Solution Explorer**e selecione **Adicionar** > **novo arquivo de** > **recursos de**itens . Nomeie o arquivo *ExceptionMessages.resx*. Este é o arquivo de recursos padrão.
1. Adicione um par de nome/valor para sua mensagem de exceção, como mostra a seguinte imagem:

   ![Adicionar recursos à cultura padrão](media/add-resources-to-default-culture.jpg)

1. Adicione um novo arquivo de recursos para francês. *Nomeie-o ExceptionMessages.fr-FR.resx*.
1. Adicione um par de nome/valor para a mensagem de exceção novamente, mas com um valor francês:

   ![Adicionar recursos à cultura fr-FR](media/add-resources-to-fr-culture.jpg)

1. Depois de construir o projeto, a pasta de saída de compilação deve conter a pasta *fr-FR* com um arquivo *.dll,* que é o conjunto de satélites.
1. Você lança a exceção com código como o seguinte:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

    ```vb
    Dim resourceManager As New ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly())
    Throw New StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John")
    ```

    > [!NOTE]
    > Se o nome `TestProject` do projeto for e o arquivo de recursos *ExceptionMessages.resx* residir na `TestProject.Resources.ExceptionMessages`pasta *Recursos* do projeto, o nome totalmente qualificado do arquivo de recurso será .

## <a name="see-also"></a>Confira também

- [Como criar exceções definidas pelo usuário](how-to-create-user-defined-exceptions.md)
- [Criando assemblies satélite para aplicativos de área de trabalho](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (Referência de C#)](../../csharp/language-reference/keywords/base.md)
- [this (Referência de C#)](../../csharp/language-reference/keywords/this.md)
