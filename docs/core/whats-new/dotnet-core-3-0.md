---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 26fb7cb25b9bf7f00f87059fbe1848763f7f175d
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415540"
---
# <a name="whats-new-in-net-core-30-preview-1"></a>Novidades do .NET Core 3.0 (versão prévia 1)

Este artigo descreve as novidades do .NET Core 3.0 (versão prévia 1). Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows). Ao utilizar um componente do .NET Core 3.0 chamado Windows Desktop, você pode fazer a portabilidade dos seus aplicativos do Windows Forms e da Windows Presentation Foundation (WPF). Para deixar claro, o componente Windows Desktop só é compatível com Windows. Para saber mais, confira a seção [Desktop Windows](#windows-desktop) abaixo.

O .NET Core 3.0 adiciona suporte para C# 8.0.

[Baixe e comece a trabalhar com o .NET Core 3 Versão prévia 1](https://aka.ms/netcore3download) agora mesmo no Windows, Mac e Linux. Você pode ver todos os detalhes da versão nas [Notas sobre a versão do .NET Core 3 Versão prévia 1](https://aka.ms/netcore3releasenotes).

Para saber mais, confira [Comunicado sobre o .NET Core 3.0 Versão prévia 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

## <a name="net-standard-21"></a>.NET Standard 2.1

O .NET Core 3.0 implementa o .NET Standard 2.1.

## <a name="default-executables"></a>Executáveis por padrão

Agora, o .NET Core criará [executáveis dependentes da estrutura](../deploying/index.md#framework-dependent-executables-fde), por padrão. Isso é novidade para aplicativos que usam uma versão do .NET Core instalada globalmente. Até agora, apenas [implantações autossuficientes](../deploying/index.md#self-contained-deployments-scd) produziam um executável.

Durante `dotnet build` ou `dotnet publish`, um arquivo executável é criado, desde que corresponda ao ambiente e à plataforma do SDK que você está usando. Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:

* Você pode clicar duas vezes no arquivo executável.
* Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.

## <a name="build-copies-dependencies"></a>O build copia dependências

`dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache do NuGet para a pasta de saída do build. Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`. 

Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.


## <a name="local-dotnet-tools"></a>Ferramentas dotnet locais

Enquanto o .NET Core 2.1 oferecia suporte para ferramentas globais, o .NET Core 3.0 agora tem ferramentas locais. As ferramentas locais são semelhantes às ferramentas globais, mas estão associadas a um local específico no disco. Isso permite ferramentas por projeto e por repositório. Qualquer ferramenta instalada localmente não está disponível globalmente.

As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual. Esse arquivo de manifesto define as ferramentas que ficarão disponíveis. Ao criar esse arquivo de manifesto na raiz do seu repositório, garanta que qualquer pessoa que clone seu código possa restaurar e usar as ferramentas necessárias para trabalhar com êxito com seu código.

Quando o arquivo de manifesto de ferramentas locais estiver disponível, use o seguinte comando para baixar e instalar essas ferramentas localmente de modo automático:

```console
dotnet tool restore
```

Execute uma ferramenta local com o seguinte comando:

```console
dotnet tool run <tool-command-name>
```

Ao chamar uma ferramenta local, o dotnet procura um manifesto na estrutura do diretório. Ao encontrar um arquivo de manifesto de ferramenta, ele é pesquisado para a ferramenta solicitada. Se a ferramenta for encontrada, ela incluirá as informações necessárias para encontrar a ferramenta no local de pacotes globais do NuGet. 

Se a ferramenta for encontrada no manifesto, mas não no cache, o usuário receberá um erro. A mensagem será aprimorada após a Versão prévia 1 para solicitar que o usuário execute `dotnet tool restore`.

Para adicionar ferramentas locais a um diretório, primeiro crie o arquivo de manifesto da ferramenta. Após a Versão prévia 1, ofereceremos um mecanismo para criar arquivos de manifesto de ferramenta, como um novo modelo dotnet. Para a Versão prévia 1, crie o arquivo chamado `dotnet-tools.json` com o seguinte conteúdo:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Após criar o manifesto, é possível adicionar ferramentas locais a ele usando:

```console
dotnet tool install <toolPackageId>
```

Esse comando instala a versão mais recente da ferramenta, a menos que outra versão seja especificada.  Mesmo se a versão mais recente for escolhida automaticamente, a versão da ferramenta será gravada no arquivo de manifesto da ferramenta para permitir que a versão correta seja restaurada ou executada.

O arquivo de manifesto da ferramenta é projetado para permitir a edição manual, o que você pode fazer para atualizar a versão necessária ao trabalhar com o repositório.

Veja aqui um exemplo de arquivo `dotnet-tools.json`:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Para remover uma ferramenta de arquivo de manifesto da ferramenta, execute o seguinte comando:

```console
dotnet tool uninstall <toolPackageId>
```

Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução. Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1. Para instalá-las global ou localmente, você ainda precisará instalar o [tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Para saber mais, consulte a [Documentação da versão prévia antecipada de ferramentas locais](https://github.com/dotnet/cli/issues/10288).

## <a name="windows-desktop"></a>Área de Trabalho do Windows

A partir do .NET Core 3.0 Versão prévia 1, é possível criar aplicativos de área de trabalho do Windows usando WPF e Windows Forms. Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).

O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.

É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:

```console
dotnet new wpf
dotnet new winforms
```

Também é possível abrir, iniciar e depurar projetos de WPF e Windows Forms do .NET Core 3.0 no Visual Studio 2019 Versão prévia 1. Atualmente, é possível abrir esses projetos no Visual Studio 2017 15.9, no entanto, esse não é um cenário compatível (e você precisará [habilitar versões prévias](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).

Os novos projetos são os mesmos que os projetos existentes do .NET Core, com algumas adições. Veja aqui a comparação entre o projeto básico de console do .NET Core e um projeto básico do Windows Forms e WPF.

Em um projeto de console do .NET Core, o projeto usa o SDK `Microsoft.NET.Sdk` e declara uma dependência no .NET Core 3.0 por meio da estrutura de destino `netcoreapp3.0`. Para criar um aplicativo de área de trabalho do Windows, use o SDK `Microsoft.NET.Sdk.WindowsDesktop` e escolha qual estrutura de interface do usuário usar:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Para escolher o Windows Forms ao invés da WPF, defina `UseWindowsForms` em vez de `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

`UseWPF` e `UseWindowsForms` podem ser definidos como `true` se o aplicativo usar ambas as estruturas; por exemplo, quando uma caixa de diálogo do Windows Forms hospeda um controle da WPF.

Compartilhe seus comentários nos repositórios [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) e [dotnet/core](https://github.com/dotnet/core/issues).

## <a name="fast-built-in-json-support"></a>Suporte interno rápido a JSON

`System.Text.Json.Utf8JsonReader` é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`. O `Utf8JsonReader` é um tipo fundamental de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados. Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do [Json.NET](https://www.newtonsoft.com/json). Ele não faz alocação até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).

Essa nova API incluirá os seguintes componentes:

* Na versão prévia 1: Leitor de JSON (acesso sequencial)
* Em breve: Gravação de JSON, DOM (acesso aleatório), serializador POCO, desserializador POCO

Veja aqui o loop de leitor básico para o `Utf8JsonReader` que pode ser usado como ponto de partida:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

O ecossistema do .NET dependia do [Json.NET](https://www.newtonsoft.com/json) e de outras bibliotecas JSON populares, que continuam a ser boas opções. O JSON.NET usa cadeias de caracteres do .NET como seu tipo de dados base, que, na verdade, são UTF-16. 

No .NET Core 2.1 e 3.0, adicionamos novas APIs que possibilitam escrever APIs JSON (como `Utf8JsonReader`) que exigem muito menos memória, com base no uso de `Span<T>` e de cadeias de caracteres UTF-8, e melhor atendem às necessidades de aplicativos de alta taxa de transferência, como Kestrel e servidores da Web do ASP.NET Core.

## <a name="ranges-and-indices"></a>Intervalos e índices

O novo tipo `Index` pode ser usado para indexação. É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Há também um tipo `Range`, que consiste em dois valores `Index`, um para o início e outro para o final, e pode ser escrito com uma expressão de intervalo `x..y` (C#). Você pode indexar com `Range` para produzir uma fatia:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> Somente o [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) oferece suporte à sintaxe para `Range` e `Index`.

## <a name="async-streams"></a>Fluxos assíncronos

O tipo `IAsyncEnumerable<T>` é uma nova versão assíncrona de `IEnumerable<T>`. A linguagem permite que você aplique `await foreach` a eles para consumir seus elementos, e aplique `yield return` a eles para produzir elementos.

O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos. A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores. Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> O .NET Core 3.0 Versão prévia 1 tem um bug com `await foreach` no momento. Ao invés disso, use `GetEnumerator` e `MoveNext` para processar elementos. Para saber mais, consulte [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).

Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`. Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.

> [!NOTE]
> Somente o [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) oferece suporte à sintaxe `await foreach`.

## <a name="type-sequencereader"></a>Tipo: SequenceReader

`System.Buffers.SequenceReader` foi adicionado ao .NET Core 3.0, podendo ser usado como um leitor para `ReadOnlySequence<T>`. Isso permite uma análise fácil, de baixa alocação e de alto desempenho dos dados `System.IO.Pipelines`, que pode cruzar vários buffers de backup. 

O exemplo a seguir quebra uma `Sequence` de entrada em linhas delimitadas `CR/LF` válidas:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Tipo: MetadataLoadContext

Adicionamos o tipo `MetadataLoadContext`, permitindo a leitura de metadados de assembly sem afetar o domínio do aplicativo do chamador. Assemblies são lidos como dados, incluindo assemblies compilados para arquiteturas e plataformas diferentes do ambiente de tempo de execução atual. `MetadataLoadContext` se sobrepõe a <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, que só está disponível no .NET Framework.

`MetdataLoadContext` está disponível no [pacote System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). Este é um pacote do .NET Standard 2.0.

O `MetadataLoadContext` expõe APIs semelhantes ao tipo <xref:System.Runtime.Loader.AssemblyLoadContext>, mas não é baseado nesse tipo. Assim como <xref:System.Runtime.Loader.AssemblyLoadContext>, o `MetadataLoadContext` permite o carregamento de assemblies dentro de um universo de carregamento de assemblies isolado. APIs `MetdataLoadContext` retornam objetos <xref:System.Reflection.Assembly>, permitindo o uso de APIs de reflexão familiares. APIs orientadas a execução, como [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), não são permitidas e emitirão InvalidOperationException.

O exemplo a seguir demonstra como localizar tipos concretos em um assembly que implementa determinada interface:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Cenários para `MetadataLoadContext` incluem recursos de tempo de design, ferramentas de tempo de build e recursos de destaque de tempo de execução, que precisam inspecionar um conjunto de assemblies como dados e ter todos os bloqueios de arquivo e memória liberados após a execução da inspeção.

Em `MetadataLoadContext`, uma classe de resolvedor é transmitida para seu construtor. O trabalho do resolvedor é carregar um `Assembly` considerando seu `AssemblyName`. A classe de resolvedor deriva da classe abstrata `MetadataAssemblyResolver`. Uma implementação do resolvedor para cenários com base em caminho é fornecida com `PathAssemblyResolver`.

Os [testes de MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstram vários casos de uso. Os [testes de assembly](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) são uma boa forma de começar.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 e OpenSSL 1.1.1 no Linux

O .NET Core agora aproveitará o [suporte do TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), quando estiver disponível em determinado ambiente. O TLS 1.3 tem vários benefícios, de acordo com a [equipe do OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Tempos de conexão aprimorados, devido a uma redução no número de viagens de ida e volta necessário entre o cliente e servidor.

* Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros e à criptografia de maior quantidade do handshake de conexão.

O .NET Core 3.0 Versão prévia 1 é capaz de utilizar **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, ou **OpenSSL 1.0.2** (seja qual for a melhor versão encontrada, em um sistema Linux).  Quando o **OpenSSL 1.1.1**  estiver disponível, os tipos SslStream e HttpClient usarão **TLS 1.3** ao usar `SslProtocols.None` (protocolos padrão do sistema), considerando que o cliente e o servidor ofereçam suporte a **TLS 1.3**.

O exemplo a seguir demonstra o .NET Core 3.0 Versão prévia 1 em Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows e macOS ainda não oferecem suporte a **TLS 1.3**. O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.

## <a name="cryptography"></a>Criptografia

Foi adicionado suporte para criptografias **AES-GCM** e **AES-CCM**, implementadas via `System.Security.Cryptography.AesGcm` e `System.Security.Cryptography.AesCcm`. Esses algoritmos são os [algoritmos de Criptografia Autenticada com Dados de Associação (AEAD) ](https://en.wikipedia.org/wiki/Authenticated_encryption) e os primeiros algoritmos de Criptografia Autenticada (AE) adicionados ao .NET Core.

O código a seguir demonstra como usar criptografia **AesGcm** para criptografar e descriptografar dados aleatórios.

O código para **AesCcm** seria quase idêntico (somente os nomes de variáveis de classe seriam diferentes).

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Importar/exportar chave de criptografia

O .NET Core 3.0 Versão prévia 1 oferece suporte à importação e exportação de chaves públicas e privadas assimétricas nos formatos padrão, sem a necessidade de usar um certificado X.509.

Todos os tipos de chave (RSA, DSA, ECDsa, ECDiffieHellman) são compatíveis com o formato **X.509 SubjectPublicKeyInfo** para chaves públicas e com os formatos **PKCS#8 PrivateKeyInfo** e **PKCS#8 EncryptedPrivateKeyInfo** para chaves privadas. RSA também é compatível com **PKCS#1 RSAPublicKey** e **PKCS#1 RSAPrivateKey**. Todos os métodos de exportação produzem dados binários codificados por DER, e os métodos de importação esperam o mesmo. Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

Arquivos PKCS#8 podem ser inspecionados com a classe `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo`.

Arquivos PFX/PKCS#12 podem ser inspecionados e manipulados com `System.Security.Cryptography.Pkcs.Pkcs12Info` e `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectivamente.

## <a name="serialport-for-linux"></a>SerialPort para Linux

O .NET Core 3.0 agora oferece suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.

Anteriormente, o .NET Core só era compatível com o uso do tipo `SerialPort` no Windows.

## <a name="more-bcl-improvements"></a>Mais melhorias do BCL

O `Span<T>`, `Memory<T>` e tipos relacionados, que foram introduzidos no .NET Core 2.1, foram otimizados no .NET Core 3.0. Operações comuns, como construção de intervalo, divisão, análise e formatação agora funcionam melhor. 

Além disso, tipos como `String` tiveram melhorias discretas para torná-los mais eficientes quando usados como chaves com `Dictionary<TKey, TValue>` e outras coleções. Nenhuma alteração de código é necessária para se beneficiar dessas melhorias.

As melhorias a seguir também são novas no .NET Core 3 Versão prévia 1:

* Suporte a Brotli integrado a HttpClient
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Operadores aritméticos complexos
* APIs de soquete para TCP em atividade
* StringBuilder.GetChunks
* Análise de IPEndPoint
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Compilação em camadas

A [compilação em camadas](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) é ativada por padrão com o .NET Core 3.0. É um recurso que permite que o tempo de execução use de forma mais adaptável o compilador Just-In-Time (JIT) para obter um melhor desempenho, tanto na inicialização quanto para maximizar a taxa de transferência.

Esse recurso foi adicionado como um recurso opcional no [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) e, em seguida, foi habilitado por padrão no [.NET Core 2.2 Versão prévia 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Subsequentemente, foi revertido novamente para opcional na versão .NET Core 2.2.

## <a name="arm64-linux-support"></a>Suporte a ARM64 no Linux

Estamos adicionando suporte a ARM64 para Linux nesta versão. Para contextualização, adicionamos suporte a ARM32 para Linux com o .NET Core 2.1 e para Windows com o .NET Core 2.2. O principal caso de uso para ARM64 atualmente é em cenários de IoT.

As imagens de [Docker Alpine, Debian e Ubuntu estão disponíveis para o .NET Core para ARM64](https://hub.docker.com/r/microsoft/dotnet/).

Consulte [Status do ARM64 do .NET Core](https://github.com/dotnet/announcements/issues/82) para saber mais.

>[!NOTE]
> O suporte do Windows a **ARM64** ainda não está disponível.
