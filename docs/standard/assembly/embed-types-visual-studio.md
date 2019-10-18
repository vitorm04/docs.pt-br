---
title: 'Walkthrough: inserir tipos de assemblies gerenciados no Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1a37a3bcc3b1bc352d6a2f59691819e0b2403d3d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523903"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>Walkthrough: inserir tipos de assemblies gerenciados no Visual Studio

Se você inserir informações de um assembly gerenciado de nome forte, você poderá acoplar vagamente tipos em um aplicativo para atingir a independência de versão. Ou seja, seu programa pode ser escrito para usar tipos de qualquer versão de uma biblioteca gerenciada sem precisar ser recompilado para cada nova versão.

A incorporação de tipo é frequentemente usada com a interoperabilidade COM, como um aplicativo que usa objetos de automação do Microsoft Office. Inserir informações de tipo permite que o mesmo build de um programa funcione com diferentes versões do Microsoft Office em diferentes computadores. No entanto, você também pode usar a inserção de tipos com soluções totalmente gerenciadas.

Depois de especificar as interfaces públicas que podem ser incorporadas, você cria classes de tempo de execução que implementam essas interfaces. Um programa cliente pode inserir as informações de tipo para as interfaces em tempo de design referenciando o assembly que contém as interfaces públicas e definindo a propriedade `Embed Interop Types` da referência a `True`. O programa cliente pode então carregar instâncias dos objetos de tempo de execução digitados como essas interfaces. Isso é equivalente a usar o compilador de linha de comando e fazer referência ao assembly usando a opção do compilador `/link`. 

Se você criar uma nova versão do assembly de tempo de execução de nome forte, o programa cliente não precisará ser recompilado. O programa cliente continua a usar qualquer versão do assembly de tempo de execução disponível para ele, usando as informações de tipo inserido para as interfaces públicas.

Neste tutorial, você:

1. Crie um assembly de nome forte com uma interface pública contendo informações de tipo que podem ser inseridas.
1. Crie um assembly de tempo de execução de nome forte que implemente a interface pública.
1. Criará um programa cliente que insere as informações de tipo da interface pública e criará uma instância da classe do assembly de tempo de execução.
1. Modificará e recompilará o assembly de tempo de execução.
1. Execute o programa cliente para ver que ele usa a nova versão do assembly de tempo de execução sem precisar ser recompilado.

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>Condições e limitações

Você pode inserir informações de tipo de um assembly sob as seguintes condições: 

- O assembly expõe pelo menos uma interface pública.
- As interfaces inseridas são anotadas com atributos de `ComImport` e atributos de `Guid` com GUIDs exclusivos.
- O assembly é anotado com o atributo `ImportedFromTypeLib` ou o atributo `PrimaryInteropAssembly` e um atributo `Guid` de nível do assembly. Os modelos C# de projeto Visual e Visual Basic incluem um atributo de `Guid` de nível de assembly por padrão.

Como a função principal do tipo incorporação é oferecer suporte a assemblies de interoperabilidade COM, as seguintes limitações se aplicam quando você insere informações de tipo em uma solução totalmente gerenciada:

- Somente atributos específicos da interoperabilidade COM são inseridos. Outros atributos são ignorados.
- Se um tipo usa parâmetros genéricos e o tipo do parâmetro genérico é um tipo inserido, esse tipo não pode ser usado em um limite de assembly. Exemplos de cruzamento de um limite de assembly incluem chamar um método de outro assembly ou derivar um tipo de um tipo definido em outro assembly.
- Constantes não são inseridas.
- A classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> não dá suporte a um tipo inserido como uma chave. Você pode implementar seu próprio tipo de dicionário para dar suporte a um tipo inserido como uma chave.

## <a name="create-an-interface"></a>Criar uma interface

A primeira etapa é criar o assembly de interface equivalente do tipo. 

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.
   
1. Na caixa de diálogo **criar um novo projeto** , digite *biblioteca de classes* na caixa **Pesquisar modelos** . Selecione o modelo C# ou a **biblioteca de classes do VB (.NET Framework)** na lista e, em seguida, selecione **Avançar**. 
   
1. Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceInterface*e, em seguida, selecione **criar**. O novo projeto é criado.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1. vb* , selecione **renomear**e renomeie o arquivo de *Class1* para *ISampleInterface*. Responda **Sim** à solicitação para também renomear a classe como `ISampleInterface`. Essa classe representa a interface pública para a classe.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**. 
   
1. Selecione **criar** no painel esquerdo da tela **Propriedades** e defina o **caminho de saída** para um local em seu computador, como *C:\TypeEquivalenceSample*. Você usa o mesmo local em todo este passo a passos. 
   
1. Selecione **assinar** no painel esquerdo da tela **Propriedades** e, em seguida, marque a caixa de seleção **assinar o assembly** . No menu suspenso para **escolher um arquivo de chave de nome forte**, selecione **novo**. 
   
1. Na caixa de diálogo **criar chave de nome forte** , em **nome do arquivo de chave**, digite *Key. SNK*. Desmarque a caixa de seleção **proteger meu arquivo de chave com uma senha** e, em seguida, selecione **OK**.
   
1. Abra o arquivo de classe *ISampleInterface* no editor de código e substitua seu conteúdo pelo código a seguir para criar a interface de `ISampleInterface`:
   
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
   
1. No menu **ferramentas** , selecione **Criar GUID**e, na caixa de diálogo **Criar GUID** , selecione **formato do registro**. Selecione **copiar**e, em seguida, selecione **sair**.
   
1. No atributo `Guid` do seu código, substitua o GUID de exemplo pelo GUID que você copiou e remova as chaves ( **{}** ).
   
1. Em **Gerenciador de soluções**, expanda a pasta **Propriedades** e selecione o arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* . No editor de código, adicione o seguinte atributo ao arquivo:
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. Selecione **arquivo**  > **salvar tudo** ou pressione **Ctrl** +**Shift** +**S** para salvar os arquivos e o projeto.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Compilar**. O arquivo DLL da biblioteca de classes é compilado e salvo no caminho de saída da compilação especificado, por exemplo, *C:\TypeEquivalenceSample*.

## <a name="create-a-runtime-class"></a>Criar uma classe de tempo de execução

Em seguida, crie a classe de tempo de execução equivalente do tipo.

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.
   
1. Na caixa de diálogo **criar um novo projeto** , digite *biblioteca de classes* na caixa **Pesquisar modelos** . Selecione o modelo C# ou a **biblioteca de classes do VB (.NET Framework)** na lista e, em seguida, selecione **Avançar**. 
   
1. Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceRuntime*e, em seguida, selecione **criar**. O novo projeto é criado.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo *Class1.cs* ou *Class1. vb* , selecione **renomear**e renomeie o arquivo de *Class1* para *SampleClass*. Responda **Sim** à solicitação para também renomear a classe como `SampleClass`. Essa classe implementa a interface `ISampleInterface`.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**. 
   
1. Selecione **criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.
   
1. Selecione **assinar** no painel esquerdo da tela **Propriedades** e, em seguida, marque a caixa de seleção **assinar o assembly** . No menu suspenso para **escolher um arquivo de chave de nome forte**, selecione **novo**. 
   
1. Na caixa de diálogo **criar chave de nome forte** , em **nome do arquivo de chave**, digite *Key. SNK*. Desmarque a caixa de seleção **proteger meu arquivo de chave com uma senha** e, em seguida, selecione **OK**.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Adicionar** **referência**de  > . 
   
1. Na caixa de diálogo **Gerenciador de referências** , selecione **procurar** e navegue até a pasta caminho de saída. Selecione o arquivo *TypeEquivalenceInterface. dll* , selecione **Adicionar**e, em seguida, selecione **OK**.
   
1. Em **Gerenciador de soluções**, expanda a pasta **referências** e selecione a referência **TypeEquivalenceInterface** . No painel **Propriedades** , defina **versão específica** como **false** se ainda não estiver.
   
1. Abra o arquivo de classe *SampleClass* no editor de código e substitua seu conteúdo pelo código a seguir para criar a classe de `SampleClass`:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
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
   
1. Selecione **arquivo**  > **salvar tudo** ou pressione **Ctrl** +**Shift** +**S** para salvar os arquivos e o projeto.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Compilar**. O arquivo DLL da biblioteca de classes é compilado e salvo no caminho de saída da compilação especificado.

## <a name="create-a-client-project"></a>Criar um projeto de cliente

Por fim, crie um programa cliente de equivalência de tipo que faça referência ao assembly da interface.

1. No Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**.
   
1. Na caixa de diálogo **criar um novo projeto** , digite *console* na caixa **Pesquisar modelos** . Selecione o modelo C# ou o **aplicativo de console do VB (.NET Framework)** na lista e, em seguida, selecione **Avançar**. 
   
1. Na caixa de diálogo **configurar seu novo projeto** , em **nome do projeto**, digite *TypeEquivalenceClient*e, em seguida, selecione **criar**. O novo projeto é criado.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Propriedades**. 
   
1. Selecione **criar** no painel esquerdo da tela **Propriedades** e, em seguida, defina o **caminho de saída** para o mesmo local usado para o projeto TypeEquivalenceInterface, por exemplo, *C:\TypeEquivalenceSample*.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceClient** e selecione **Adicionar** **referência**de  > . 
   
1. Na caixa de diálogo **Gerenciador de referências** , se o arquivo **TypeEquivalenceInterface. dll** já estiver listado, selecione-o. Caso contrário, selecione **procurar**, navegue até a pasta caminho de saída, selecione o arquivo *TypeEquivalenceInterface. dll* (não o *TypeEquivalenceRuntime. dll*) e selecione **Adicionar**. Selecione **OK**.
   
1. Em **Gerenciador de soluções**, expanda a pasta **referências** e selecione a referência **TypeEquivalenceInterface** . No painel **Propriedades** , defina **inserir tipos de interoperabilidade** como **true**.
   
1. Abra o arquivo *Program.cs* ou *Module1. vb* no editor de código e substitua seu conteúdo pelo código a seguir para criar o programa cliente:
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
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
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
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
   
1. Selecione **arquivo**  > **salvar tudo** ou pressione **Ctrl** +**Shift** +**S** para salvar os arquivos e o projeto.
   
1. Pressione **Ctrl** +**F5** para compilar e executar o programa. Observe que a saída do console retorna a versão **1.0.0.0**do assembly. 
   
## <a name="modify-the-interface"></a>Modificar a interface

Agora, modifique o assembly da interface e altere sua versão. 

1. No Visual Studio, selecione **arquivo**  > **abrir**  > **projeto/solução**e abra o projeto **TypeEquivalenceInterface** .
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Propriedades**. 
   
1. Selecione **aplicativo** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **informações do assembly**. 
   
1. Na caixa de diálogo **informações do assembly** , altere a **versão do assembly** e os valores de **versão do arquivo** para *2.0.0.0*e selecione **OK**.
   
1. Abra o arquivo *SampleInterface.cs* ou *SampleInterface. vb* e adicione a seguinte linha de código à interface `ISampleInterface`:
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. Selecione **arquivo**  > **salvar tudo** ou pressione **Ctrl** +**Shift** +**S** para salvar os arquivos e o projeto.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceInterface** e selecione **Compilar**. Uma nova versão do arquivo DLL da biblioteca de classes é compilada e salva no caminho de saída da compilação.

## <a name="modify-the-runtime-class"></a>Modificar a classe de tempo de execução

Além disso, modifique a classe Runtime e atualize sua versão. 

1. No Visual Studio, selecione **arquivo**  > **abrir**  > **projeto/solução**e abra o projeto **TypeEquivalenceRuntime** .
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Propriedades**. 
   
1. Selecione **aplicativo** no painel esquerdo da tela **Propriedades** e, em seguida, selecione **informações do assembly**. 
   
1. Na caixa de diálogo **informações do assembly** , altere a **versão do assembly** e os valores de **versão do arquivo** para *2.0.0.0*e selecione **OK**.
   
1. Abra o arquivo *SampleClass.cs* ou *SampleClass. vb* e adicione o seguinte código à classe `SampleClass`:
   
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
   
1. Selecione **arquivo**  > **salvar tudo** ou pressione **Ctrl** +**Shift** +**S** para salvar os arquivos e o projeto.
   
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **TypeEquivalenceRuntime** e selecione **Compilar**. Uma nova versão do arquivo DLL da biblioteca de classes é compilada e salva no caminho de saída da compilação.

## <a name="run-the-updated-client-program"></a>Executar o programa cliente atualizado 

Vá para o local da pasta de saída da compilação e execute *TypeEquivalenceClient. exe*. Observe que a saída do console agora reflete a nova versão do assembly `TypeEquivalenceRuntime`, *2.0.0.0*, sem que o programa seja recompilado.

## <a name="see-also"></a>Consulte também

- [-link (opções do compilador do C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Programa com assemblies](program.md)
- [Assemblies no .NET](index.md)
