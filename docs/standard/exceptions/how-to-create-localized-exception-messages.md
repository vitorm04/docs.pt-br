---
title: 'Como: criar exceções definidas pelo usuário com mensagens de exceção localizadas'
description: Saiba como criar exceções definidas pelo usuário com mensagens de exceção localizadas
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: 1e5ef5658e4cb71d0689a1786494eaec57d4e7fb
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332987"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>Como: criar exceções definidas pelo usuário com mensagens de exceção localizadas

Neste artigo, você aprenderá a criar exceções definidas pelo usuário que são herdadas da classe base <xref:System.Exception> com mensagens de exceção localizadas usando assemblies satélite.

## <a name="create-custom-exceptions"></a>Criar exceções personalizadas

O .NET contém muitas exceções diferentes que você pode usar. No entanto, em alguns casos, quando nenhum deles atende às suas necessidades, você pode criar suas próprias exceções personalizadas.

Vamos supor que você deseja criar um `StudentNotFoundException` que contenha uma propriedade `StudentName`.
Para criar uma exceção personalizada, siga estas etapas:

1. Crie uma classe serializável que herde de <xref:System.Exception>. O nome da classe deve terminar em "Exception":

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. Adicione os construtores padrão:

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

## <a name="create-localized-exception-messages"></a>Criar mensagens de exceção localizadas

Você criou uma exceção personalizada e pode jogá-la em qualquer lugar com um código semelhante ao seguinte:

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

O problema com a linha anterior é que "o aluno não pode ser encontrado". é apenas uma cadeia de caracteres constante. Em um aplicativo localizado, você deseja ter mensagens diferentes dependendo da cultura do usuário.
Os [assemblies satélite](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md) são uma boa maneira de fazer isso. Um assembly satélite é uma. dll que contém recursos para um idioma específico. Quando você solicita recursos específicos em tempo de execução, o CLR encontra esse recurso dependendo da cultura do usuário. Se nenhum assembly satélite for encontrado para essa cultura, os recursos da cultura padrão serão usados.

Para criar as mensagens de exceção localizadas:

1. Crie uma nova pasta chamada *recursos* para armazenar os arquivos de recurso.
1. Adicione um novo arquivo de recurso a ele. Para fazer isso no Visual Studio, clique com o botão direito do mouse na pasta em **Gerenciador de soluções**e selecione **Adicionar** -> **novo item** -> **arquivo de recursos**. Nomeie o arquivo *ExceptionMessages. resx*. Esse é o arquivo de recursos padrão.
1. Adicione um par de nome/valor à mensagem de exceção, como mostra a imagem a seguir: recursos de @no__t 0Add para a cultura padrão @ no__t-1
1. Adicione um novo arquivo de recurso para francês. Nomeie-o *ExceptionMessages.fr-fr. resx*.
1. Adicione um par nome/valor à mensagem de exceção novamente, mas com um valor em francês: recursos de @no__t 0Add para a cultura fr-FR @ no__t-1
1. Depois de compilar o projeto, a pasta de saída da compilação deve conter a pasta *fr-fr* com um arquivo *. dll* , que é o assembly satélite.
1. Você lança a exceção com um código semelhante ao seguinte:

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > Se o nome do projeto for `TestProject` e o arquivo de recurso *ExceptionMessages. resx* residir na pasta *Resources* do projeto, o nome totalmente qualificado do arquivo de recurso será `TestProject.Resources.ExceptionMessages`.

## <a name="see-also"></a>Consulte também

- [Como criar exceções definidas pelo usuário](how-to-create-user-defined-exceptions.md)
- [Criando assemblies satélite para aplicativos da área de trabalho](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [base (C# referência)](../../csharp/language-reference/keywords/base.md)
- [isso (C# referência)](../../csharp/language-reference/keywords/this.md)
