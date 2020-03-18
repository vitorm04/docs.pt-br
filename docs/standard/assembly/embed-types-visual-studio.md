---
title: 'Passo a passo: Incorporar tipos de montagens gerenciadas no Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338551"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Passo a passo: Incorporar tipos de montagens gerenciadas no Visual Studio

Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão. Ou seja, seu programa pode ser escrito para usar tipos de qualquer versão de uma biblioteca gerenciada sem ter que ser recompilado para cada nova versão.

A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office. Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores. No entanto, você também pode usar incorporação de tipo com soluções totalmente gerenciadas.

Depois de especificar as interfaces públicas que podem ser incorporadas, você cria classes de tempo de execução que implementam essas interfaces. Um programa cliente pode incorporar as informações do tipo para as interfaces no momento do `Embed Interop Types` projeto, fazendo `True`referência ao conjunto que contém as interfaces públicas e definindo a propriedade da referência a . O programa cliente pode então carregar instâncias dos objetos de tempo de execução digitados como essas interfaces. Isso equivale a usar o compilador de linha de comando e referenciar o conjunto usando a [opção -link compilador](../../csharp/language-reference/compiler-options/link-compiler-option.md).

Se você criar uma nova versão do seu conjunto de tempo de execução com nome forte, o programa cliente não precisa ser recompilado. O programa cliente continua a usar qualquer versão do conjunto de tempo de execução disponível para ele, usando as informações do tipo incorporado para as interfaces públicas.

Neste passo a passo, você vai:

1. Crie um conjunto com nome forte com uma interface pública contendo informações de tipo que podem ser incorporadas.
1. Crie um conjunto de tempo de execução com nome forte que implemente a interface pública.
1. Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de runtime.
1. Modificará e recompilará o assembly de runtime.
1. Execute o programa cliente para ver se ele usa a nova versão do conjunto de tempo de execução sem ter que ser recompilado.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Condições e limitações

Você pode incorporar informações de tipo a partir de um conjunto nas seguintes condições:

- O assembly expõe pelo menos uma interface pública.
- As interfaces incorporadas são `ComImport` anotadas `Guid` com atributos e atributos com GUIDs exclusivos.
- O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly. Os modelos de projeto Visual C# e `Guid` Visual Basic incluem um atributo de nível de montagem por padrão.

Como a função principal da incorporação de tipos é o suporte a conjuntos de interop COM, as seguintes limitações se aplicam quando você incorpora informações de tipo em uma solução totalmente gerenciada:

- Apenas atributos específicos para com interop são incorporados. Outros atributos são ignorados.
- Se um tipo usa parâmetros genéricos, e o tipo do parâmetro genérico é um tipo incorporado, esse tipo não pode ser usado através de um limite de montagem. Exemplos de cruzar um limite de montagem incluem chamar um método de outro conjunto ou derivar um tipo de um tipo definido em outro conjunto.
- Constantes não são inseridas.
- A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave. Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.

## <a name="create-an-interface"></a>Criar uma interface

O primeiro passo é criar o conjunto de interface de equivalência do tipo.

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.

1. Na **caixa Criar uma nova** caixa de diálogo de projeto, digite biblioteca de *classes* na caixa **Procurar modelos.** Selecione o modelo C# ou Visual Basic **Class Library (.NET Framework)** da lista e selecione **Next**.

1. Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceInterface*e, em seguida, selecione **Criar**. Quando um novo projeto é criado.

1. No **Solution Explorer,** clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1.vb,* selecione **Renomear**e renomeie o arquivo de *Class1* para *ISampleInterface*. Responda **Sim** ao prompt para também `ISampleInterface`renomear a classe para . Esta classe representa a interface pública para a classe.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e, em seguida, selecione **Propriedades**.

1. Selecione **Construir** no painel esquerdo da tela **Propriedades** e definir o **caminho de saída** para um local no computador, como *C:\TypeEquivalenceSample*. Você usa o mesmo local durante este passo a passo.

1. Selecione **Assinar** no painel esquerdo da tela **Propriedades** e, em seguida, selecione a caixa De **seleção Assinar.** No dropdown para **Escolher um arquivo de chave de nome forte,** selecione **Novo**.

1. Na **caixa de diálogo Criar chave de nome** forte, em Nome de **chave,** digite *key.snk*. Desmarque o **arquivo proteger minha chave com uma** caixa de seleção de senha e, em seguida, selecione **OK**.

1. Abra o arquivo de classe *ISampleInterface* no editor de código e `ISampleInterface` substitua seu conteúdo pelo seguinte código para criar a interface:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. No menu **Ferramentas,** selecione **Criar Guia**e, na caixa de diálogo **Criar guid,** selecione **Formato de Registro**. Selecione **Copiar**e, em seguida, selecione **Sair**.

1. No `Guid` atributo do seu código, substitua a guia de amostra pelo GUID copiado e remova os aparelhos (**{ }**).

1. No **Solution Explorer,** expanda a pasta **Propriedades** e selecione o *arquivo AssemblyInfo.cs* ou *AssemblyInfo.vb.* No editor de código, adicione o seguinte atributo ao arquivo:

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Build**. O arquivo DLL da biblioteca de classe é compilado e salvo no caminho de saída de compilação especificado, por exemplo *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Crie uma classe de tempo de execução

Em seguida, crie a classe de tempo de execução de equivalência de equivalência do tipo.

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.

1. Na **caixa Criar uma nova** caixa de diálogo de projeto, digite biblioteca de *classes* na caixa **Procurar modelos.** Selecione o modelo C# ou Visual Basic **Class Library (.NET Framework)** da lista e selecione **Next**.

1. Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceRuntime*e selecione **Criar**. Quando um novo projeto é criado.

1. No **Solution Explorer,** clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1.vb,* selecione **Renomear**e renomeie o arquivo de *Class1* para *SampleClass*. Responda **Sim** ao prompt para também `SampleClass`renomear a classe para . Essa classe implementa a interface `ISampleInterface`.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.

1. Selecione **Criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.

1. Selecione **Assinar** no painel esquerdo da tela **Propriedades** e, em seguida, selecione a caixa De **seleção Assinar.** No dropdown para **Escolher um arquivo de chave de nome forte,** selecione **Novo**.

1. Na **caixa de diálogo Criar chave de nome** forte, em Nome de **chave,** digite *key.snk*. Desmarque o **arquivo proteger minha chave com uma** caixa de seleção de senha e, em seguida, selecione **OK**.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Adicionar** > **referência**.

1. Na caixa **de diálogo Gerenciador de** referência, **selecione Procurar** e navegar até a pasta de caminho de saída. Selecione o *arquivo TypeEquivaleInterface.dll,* selecione **Adicionar**e, em seguida, selecione **OK**.

1. No **Solution Explorer,** expanda a pasta **Referências** e selecione a referência **TypeEquivalenceInterface.** No painel **Propriedades,** defina **Versão Específica** como **Falsa** se ela ainda não estiver.

1. Abra o arquivo de classe *SampleClass* no editor de código e `SampleClass` substitua seu conteúdo pelo seguinte código para criar a classe:

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Build**. O arquivo DLL da biblioteca de classe é compilado e salvo no caminho de saída de compilação especificado.

## <a name="create-a-client-project"></a>Crie um projeto cliente

Finalmente, crie um programa cliente de equivalência de tipo que faz referência ao conjunto de interfaces.

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.

1. Na **caixa Criar uma nova** caixa de diálogo de projeto, digite console na caixa Procurar **modelos.** *console* Selecione o modelo C# ou Visual Basic **Console App (.NET Framework)** da lista e selecione **Next**.

1. Na **caixa de diálogo Configurar sua nova** caixa de diálogo de projeto, em nome do **projeto,** *digite TypeEquivalenceClient*e, em seguida, selecione **Criar**. Quando um novo projeto é criado.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Propriedades**.

1. Selecione **Criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Adicionar** > **referência**.

1. Na caixa **de diálogo Gerenciador de** referência, se o arquivo **TypeEquivalenceInterface.dll** já estiver listado, selecione-o. Se não, **selecione Procurar**, navegue na pasta de caminho de saída, selecione o arquivo *TypeEquivalenceInterface.dll* (não o *TypeEquivalenceRuntime.dll)* e selecione **Adicionar**. Selecione **OK**.

1. No **Solution Explorer,** expanda a pasta **Referências** e selecione a referência **TypeEquivalenceInterface.** No painel **Propriedades,** defina **Os Tipos de Interop** de Incorporar como **True**.

1. Abra o arquivo *Program.cs* ou *Module1.vb* no editor de código e substitua seu conteúdo pelo seguinte código para criar o programa cliente:

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.

1. Pressione **Ctrl**+**F5** para construir e executar o programa. Observe que a saída do console retorna a versão de montagem **1.0.0.0**.

## <a name="modify-the-interface"></a>Modificar a interface

Agora, modifique o conjunto de interface e altere sua versão.

1. No Visual Studio, selecione > **Projeto/Solução Aberta de** > **Project/Solution** **Arquivo**e abra o projeto **TypeEquivalenceInterface.**

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**.

1. Selecione **''Aplicativo'** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **'Informações de montagem '''**

1. Na caixa de diálogo Informações de **montagem,** altere os valores da **versão Assembly** e **file** para *2.0.0.0*e selecione **OK**.

1. Abra o *arquivo SampleInterface.cs* ou *SampleInterface.vb* e adicione `ISampleInterface` a seguinte linha de código à interface:

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Build**. Uma nova versão do arquivo DLL da biblioteca de classe é compilada e salva no caminho de saída de compilação.

## <a name="modify-the-runtime-class"></a>Modifique a classe de tempo de execução

Também modifique a classe de tempo de execução e atualize sua versão.

1. No Visual Studio, selecione > **Projeto/Solução Aberta de** > **Project/Solution** **Arquivo**e abra o projeto **TypeEquivalenceRuntime.**

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Propriedades**.

1. Selecione **''Aplicativo'** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **'Informações de montagem '''**

1. Na caixa de diálogo Informações de **montagem,** altere os valores da **versão Assembly** e **file** para *2.0.0.0*e selecione **OK**.

1. Abra o *arquivo SampleClass.cs* ou *SampleClass.vb* e `SampleClass` adicione o seguinte código à classe:

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. Selecione **'Salvar o** > **arquivo'** ou **pressione Ctrl**+**Shift**+**S** para salvar os arquivos e o projeto.

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Build**. Uma nova versão do arquivo DLL da biblioteca de classe é compilada e salva no caminho de saída de compilação.

## <a name="run-the-updated-client-program"></a>Execute o programa cliente atualizado

Vá para o local da pasta de saída de compilação e execute *TypeEquivalenceClient.exe*. Note que a saída do console `TypeEquivalenceRuntime` agora reflete a nova versão do conjunto, *2.0.0.0*, sem que o programa seja recompilado.

## <a name="see-also"></a>Confira também

- [-link (C# Opções de compilador)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies no .NET](index.md)
