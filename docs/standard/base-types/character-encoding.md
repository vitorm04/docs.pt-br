---
title: "Codificação de caracteres no .NET"
description: "Codificação de caracteres no .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e72540726bdd1b3624064c7388e58d80320c5831

---

# <a name="character-encoding-in-net"></a>Codificação de caracteres no .NET

Os caracteres são entidades abstratas que podem ser representadas de muitas maneiras diferentes. Uma codificação de caracteres é um sistema que emparelha cada caractere em um conjunto de caracteres com suporte com algum valor que representa esse caractere. Por exemplo, o código Morse é uma codificação de caracteres que emparelha cada caractere do alfabeto romano com um padrão de pontos e traços adequados para transmissão por linhas telegráficas. Uma codificação de caracteres para computadores emparelha cada caractere em um conjunto de caracteres com suporte com um valor numérico que representa esse caractere. Uma codificação de caracteres tem dois componentes distintos:

* Um codificador, que converte uma sequência de caracteres em uma sequência de valores numéricos (bytes).

* Um decodificador, que converte uma sequência de bytes em uma sequência de caracteres.

A codificação de caracteres descreve as regras por meio das quais um codificador e um decodificador são operados. Por exemplo, a classe [UTF8Encoding](xref:System.Text.UTF8Encoding) descreve as regras de codificação para UTF-8 (Formato de Transformação Unicode de 8 bits), e de decodificação desse formato, que usa de um a quatro bytes para representar um único caractere Unicode. Codificar e decodificar também podem incluir a validação. Por exemplo, a classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding) verifica todos os substitutos para certificar-se de eles constituem pares alternativos válidos. (Um par alternativo consiste em um caractere com um ponto de código que varia de U+D800 a U+DBFF seguido por um caractere com um ponto de código que varia de U+DC00 a U+DFFF.) Uma estratégia de fallback determina como um codificador lida com caracteres inválidos ou como um decodificador lida com bytes inválidos. 

> [!WARNING]
> As classes de codificação .NET fornecem uma maneira de armazenar e converter dados de caractere. Elas não devem ser usadas para armazenar dados binários no formato de cadeia de caracteres. Dependendo da codificação usada, a conversão de dados binários em formato de cadeia de caracteres com classes de codificação pode introduzir um comportamento inesperado e produzir dados imprecisos ou corrompidos. Para converter dados binários em um formato de cadeia de caracteres, use o método [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])). 
 
O .NET usa a codificação UTF-16 (representado pela classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) para representar caracteres e cadeias de caracteres. Aplicativos que segmentam o Common Language Runtime e usam codificadores para mapear representações de caracteres Unicode com suporte pelo common language runtime para outros esquemas de codificação. Eles usam decodificadores para mapear caracteres de codificações não Unicode para Unicode.

Este tópico é composto pelas seguintes seções:

* [Codificações no .NET](#encodings-in-net)

* [Selecionando uma classe de codificação](#selecting-an-encoding-class)

* [Usando um objeto de codificação](#using-an-encoding-object)

* [Escolhendo uma estratégia de fallback](#choosing-a-fallback-strategy)

* [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a>Codificações no .NET

Todos as classes de codificação de caracteres no .NET são herdadas da classe [System.Text.Encoding](xref:System.Text.Encoding), uma classe abstrata que define a funcionalidade comum a todas as codificações de caracteres. Para acessar os objetos de codificação individuais implementados no .NET, faça o seguinte:

* Usar propriedades estáticas da classe [Encoding](xref:System.Text.Encoding), que retornam objetos que representam as codificações de caracteres padrão disponíveis no .NET (ASCII, UTF-7, UTF-8, UTF-16 e UTF-32). Por exemplo, a propriedade [Encoding. Unicode](xref:System.Text.Encoding.Unicode) retorna um objeto [UnicodeEncoding](xref:System.Text.UnicodeEncoding). Cada objeto usa o fallback de substituição para lidar com cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar. (Para obter mais informações, consulte a seção [Fallback de substituição](#replacement-fallback).)

* Chame o construtor de classe da codificação. A instância de objetos para as codificações ASCII, UTF-7, UTF-8, UTF-16 e UTF-32 podem ser criadas dessa forma. Por padrão, cada objeto usa fallback de substituição para manipular as cadeias de caracteres que ele não consegue codificar e bytes que ele não consegue decodificar, mas, em vez disso, você pode especificar que uma exceção seja gerada. (Para obter mais informações, consulte as seções [Fallback de substituição](#replacement-fallback) e [Fallback de exceção](#exception-fallback).)

* Chame o construtor [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) e passe por ele um inteiro que represente a codificação. Os objetos de codificação padrão usam o fallback de substituição e a página de código e o DBCS (conjunto de caracteres de dois bytes) que codificam objetos usam o fallback que melhor se ajusta para manipular cadeias de caracteres que eles não conseguem codificar e bytes que eles não conseguem decodificar. (Para obter mais informações, consulte a seção [Fallback de melhor ajuste](#best-fit-fallback).)

* Chame o método [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)), que retorna qualquer padrão, página de código ou codificação DBCS disponível no .NET. As sobrecargas permitem especificar um objeto de fallback para o codificador e o decodificador.

> [!NOTE]
> O padrão Unicode atribui um ponto de código (um número) e um nome a cada caractere em todos os scripts com suporte. Por exemplo, o caractere "A" é representado pelo ponto de código de U+0041 e o nome "LETRA MAIÚSCULA LATINA A". As codificações UTF (Unicode Transformation Format) definem maneiras de codificar esse ponto de código em uma sequência de um ou mais bytes. Um esquema de codificação Unicode simplifica o desenvolvimento de aplicativos prontos para o mundo, porque ele permite que qualquer conjunto de caracteres sejam representados em uma única codificação. Os desenvolvedores de aplicativos não precisam mais controlar o esquema de codificação usado para gerar caracteres para um idioma específico ou sistema de gravação e os dados podem ser compartilhados entre sistemas internacionalmente sem serem corrompidos.
>
>  O .NET dá suporte a três codificações definidas pelo padrão Unicode: UTF-8, UTF-16 e UTF-32. Para obter mais informações, consulte Padrão Unicode na página inicial [Unicode](http://www.unicode.org/).
 
O .NET dá suporte aos sistemas de codificação de caracteres listados na tabela a seguir.

Codificando | Classe | Descrição | Vantagens/desvantagens
-------- | ----- | ----------- | ------------------------ 
ASCII | [ASCIIEncoding](xref:System.Text.ASCIIEncoding) | Codifica um intervalo limitado de caracteres usando os menores sete bits de um byte. | Como essa codificação só dá suporte a valores de caracteres de U+0000 a U+007F, na maioria dos casos, ela é inadequada para aplicativos internacionalizados.
UTF-7 | [UTF7Encoding](xref:System.Text.UTF7Encoding) | Representa caracteres como sequências de caracteres ASCII de 7 bits. Caracteres Unicode não ASCII são representados por uma sequência de escape de caracteres ASCII. | O UTF-7 dá suporte a protocolos como email e protocolos de grupos de notícias. No entanto, o UTF-7 não é particularmente seguro ou robusto. Em alguns casos, alterar um bit pode alterar radicalmente a interpretação de toda uma cadeia de caracteres UTF-7. Em outros casos, diferentes cadeias de caracteres UTF-7 podem codificar o mesmo texto. Para as sequências que incluem caracteres não ASCII, o UTF-7 requer mais espaço do que o UTF-8 e a codificação/decodificação é mais lenta. Consequentemente, você deve usar o UTF-8 em vez do UTF-7, se possível.
UTF-8 | [UTF8Encoding](xref:System.Text.UTF8Encoding) | Representa cada ponto de código Unicode como uma sequência de um a quatro bytes. | O UTF-8 dá suporte a tamanhos de dados de 8 bits e funciona bem com muitos sistemas operacionais existentes. Para o intervalo de caracteres ASCII, o UTF-8 é idêntico à codificação ASCII e permite um conjunto mais amplo de caracteres. No entanto, para scripts CJK (chinês-japonês-coreano), o UTF-8 pode exigir três bytes para cada caractere e pode eventualmente gerar tamanhos de dados maiores do que o UTF-16. Observe que, às vezes, a quantidade de dados ASCII, como tags HTML, justifica o tamanho maior do intervalo CJK.
UTF-16 | [UnicodeEncoding](xref:System.Text.UnicodeEncoding) | Representa cada ponto de código Unicode como uma sequência de um a dois inteiros de 16 bits. Os caracteres Unicode mais comuns exigem apenas um ponto de código UTF-16, embora os caracteres suplementares Unicode (U+10000 e maiores) exigem dois pontos de código UTF-16 alternativos. Há suporte para as ordens de byte little endian e big endian. | A codificação UTF-16 é usada pelo Common Language Runtime para representar os valores Char e String e é usada pelo sistema operacional Windows para representar valores WCHAR.
UTF-32 | [UTF32Encoding](xref:System.Text.UTF32Encoding) | Representa cada ponto de código Unicode como um inteiro de 32 bits. Há suporte para as ordens de byte little endian e big endian. | A codificação UTF-32 é usada quando aplicativos desejam evitar o comportamento do ponto de código alternativo de codificação UTF-16 em sistemas operacionais para os quais o espaço codificado é muito importante. Glifos únicos renderizados em uma tela ainda podem ser codificados com mais de um caractere UTF-32.

Essas codificações permitem que você trabalhe com caracteres Unicode, bem como com codificações mais comumente usadas em aplicativos herdados. Além disso, você pode criar uma codificação personalizada definindo uma classe que deriva de [Encoding](xref:System.Text.Encoding) e substituindo seus membros.

> [!NOTE]
> Por padrão, o .NET Core não disponibiliza nenhuma codificação de página de código diferente de página de código 28591 e das codificações Unicode, como UTF-8 e UTF-16. No entanto, você pode adicionar as codificações de página de código encontradas em aplicativos do Windows padrão que direcionam o .NET Framework ao seu aplicativo. Para obter informações completas, consulte o tópico [EncodingProvider](xref:System.Text.EncodingProvider). 

## <a name="selecting-an-encoding-class"></a>Selecionando uma classe de codificação

Se você tiver a oportunidade de escolher a codificação a ser usada pelo seu aplicativo, você deverá usar a codificação Unicode, preferencialmente [UTF8Encoding](xref:System.Text.UTF8Encoding) ou [UnicodeEncoding](xref:System.Text.UnicodeEncoding). (O .NET também dá suporte a uma terceira codificação Unicode, [UTF32Encoding](xref:System.Text.UTF32Encoding).) 

Se você estiver planejando usar uma codificação ASCII ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), escolha [UTF8Encoding](xref:System.Text.UTF8Encoding) em vez disso. As duas codificações são idênticas para o conjunto de caracteres ASCII, mas o [UTF8Encoding](xref:System.Text.UTF8Encoding) tem as seguintes vantagens: 

* Ele pode representar todos os caracteres Unicode, enquanto o [ASCIIEncoding](xref:System.Text.ASCIIEncoding) dá suporte apenas aos valores de caracteres Unicode entre U+0000 e U+007F.

* Ele fornece detecção de erros e melhor segurança.

* Ele foi ajustado para ser o mais rápido possível e deve ser mais rápido do que qualquer outra codificação. Mesmo para o conteúdo totalmente ASCII, as operações executadas com o [UTF8Encoding](xref:System.Text.UTF8Encoding) são mais rápidas que as operações executadas com o [ASCIIEncoding](xref:System.Text.ASCIIEncoding).

Você deve considerar usar o [ASCIIEncoding](xref:System.Text.ASCIIEncoding) apenas para aplicativos herdados. No entanto, mesmo para aplicativos herdados, o [UTF8Encoding](xref:System.Text.UTF8Encoding) pode ser uma escolha melhor pelos seguintes motivos (supondo as configurações padrão):

* Se seu aplicativo tiver conteúdo que não é estritamente ASCII e codificá-lo com o [ASCIIEncoding](xref:System.Text.ASCIIEncoding), cada caractere não ASCII codificará como um ponto de interrogação (?). Se o aplicativo decodificar esses dados, as informações serão perdidas.


* Se seu aplicativo tiver conteúdo que não é estritamente ASCII e codificá-lo com o [UTF8Encoding](xref:System.Text.UTF8Encoding), o resultado parecerá ininteligível se interpretado como ASCII. No entanto, se o aplicativo usar um decodificador de UTF-8 para decodificar esses dados, os dados executarão uma viagem de ida e volta com êxito.

Em um aplicativo Web, os caracteres enviados ao cliente em resposta a uma solicitação da Web devem refletir a codificação usada no cliente. Na maioria dos casos, você deve definir a propriedades [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) como o valor retornado pela propriedade [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) para exibir texto na codificação que o usuário espera.

## <a name="using-an-encoding-object"></a>Usando um objeto de codificação

Um codificador converte uma cadeia de caracteres (mais comumente, caracteres Unicode) em seu equivalente numérico (byte). Por exemplo, você pode usar um codificador ASCII para converter caracteres Unicode em ASCII para que eles possam ser exibidos no console. Para executar a conversão, você chama o método [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])). Se você desejar determinar quantos bytes são necessários para armazenar os caracteres codificados antes de executar a codificação, você poderá chamar o método [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])).

O exemplo a seguir usa uma matriz de byte único para codificar cadeias de caracteres em duas operações separadas. Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de bytes codificados em ASCII. Ela chama o método [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) para garantir que a matriz de bytes seja grande o suficiente para acomodar a cadeia de caracteres codificada. Depois, ela chama o método [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) para codificar caracteres na cadeia de caracteres.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

Um decodificador converte uma matriz de bytes que reflete uma codificação de caracteres específica em um conjunto de caracteres, seja em uma matriz de caracteres ou em uma cadeia de caracteres. Para decodificar uma matriz de bytes em uma matriz de caracteres, chame o método [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])). Para decodificar uma matriz de bytes em uma cadeia de caracteres, chame o método [GetString](xref:System.Text.Encoding.GetString(System.Byte[])). Se você desejar determinar quantos caracteres são necessários para armazenar os bytes decodificados antes de executar a decodificação, você poderá chamar o método [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])).

O exemplo a seguir codifica três cadeias de caracteres e, em seguida, as decodifica em uma única matriz de caracteres. Ela mantém um índice que indica a posição inicial na matriz de bytes para o próximo conjunto de caracteres codificados. Ela chama o método [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) para garantir que a matriz de caracteres seja grande o suficiente para acomodar todos os caracteres decodificados. Depois, ela chama o método [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) para decodificar a matriz de bytes.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

Os métodos de codificação e decodificação de uma classe derivada de [Encoding](xref:System.Text.Encoding) foram criados para funcionar em um conjunto completo de dados; ou seja, todos os dados a serem codificados ou decodificados são fornecido em uma única chamada de método. No entanto, em alguns casos, os dados estão disponíveis em um fluxo e os dados a serem codificados ou decodificados podem estar disponíveis somente em operações de leitura separadas. Isso requer a operação de codificação ou decodificação para lembrar qualquer estado salvo em sua invocação anterior. Métodos de classes derivados de [Encoder](xref:System.Text.Encoder) e [Decoder](xref:System.Text.Decoder) são capazes de lidar com as operações de codificação e decodificação que abrangem várias chamadas de método.

Um objeto [Encoder](xref:System.Text.Encoder) de uma determinada codificação está disponível na propriedade [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) dessa codificação. Um objeto [Decoder](xref:System.Text.Decoder) da uma determinada codificação está disponível na propriedade [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) dessa codificação. Para operações de decodificação, observe que as classes derivadas de [Decoder](xref:System.Text.Decoder) incluem um método [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)), mas elas não têm um método que corresponde a [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).

O exemplo a seguir ilustra a diferença entre usar os métodos [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) e [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) para decodificar uma matriz de bytes Unicode. O exemplo codifica uma cadeia de caracteres que contém alguns caracteres Unicode em um arquivo e, em seguida, usa os dois métodos de decodificação para decodificá-los dez bytes por vez. Como um par alternativo ocorre nos bytes décimo e décimo primeiro, ele é decodificado em chamadas de método separadas. Como mostra a saída, o método [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) não é capaz de decodificar corretamente os bytes e, em vez disso, os substitui por U+FFFD (CARACTERE DE SUBSTITUIÇÃO). Por outro lado, o método [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) é capaz de decodificar com êxito a matriz de bytes para obter a cadeia de caracteres original.

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a>Escolhendo uma estratégia de fallback

Quando um método tenta codificar ou decodificar um caractere, mas não existe nenhum mapeamento, ele deve implementar uma estratégia de fallback que determine como o mapeamento com falha deva ser tratado. Há três tipos de estratégias de fallback: 

* Fallback de melhor ajuste

* Fallback de substituição

* Fallback de exceção

> [!IMPORTANT]
> Os problemas mais comuns em operações de codificação ocorrem quando um caractere Unicode não pode ser mapeado para uma determinada codificação de página de código. Os problemas mais comuns em operações de decodificação ocorrem quando sequências de bytes inválidas não podem ser convertidas em caracteres Unicode válidos. Por esses motivos, você deve saber qual estratégia de fallback um objeto de codificação específico usa. Sempre que possível, você deve especificar a estratégia de fallback usada por um objeto de codificação quando você criar uma instância do objeto.
 
### <a name="best-fit-fallback"></a>Fallback de melhor ajuste

Quando um caractere não tiver uma correspondência exata na codificação de destino, o codificador pode tentar mapeá-lo para um caractere semelhante. (O fallback de melhor ajuste é sobretudo uma codificação em vez de um problema de decodificação. Há poucas páginas de código que contêm caracteres que não podem ser mapeados com êxito para Unicode.) O fallback de melhor ajuste é o padrão para a página de código e para codificações de conjuntos de caracteres recuperados pelas sobrecargas [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) e [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)).

> [!NOTE]
> Na teoria, as classes de codificação Unicode fornecidas no .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding) e [UTF32Encoding](xref:System.Text.UTF32Encoding)) dão suporte a todos os caracteres em cada conjunto de caracteres para que eles possam ser usados para eliminar problemas de fallback de melhor ajuste. 
 

As estratégias de melhor ajuste variam de acordo com as diferentes páginas de código e não são documentadas detalhadamente. Por exemplo, para algumas páginas de código, caracteres latinos de largura inteira mapeiam para os caracteres latinos de meia largura mais comuns. Para outras páginas de código, esse mapeamento não é feito. Mesmo em uma estratégia de melhor ajuste agressiva, não há nenhum ajuste imaginável para alguns caracteres em algumas codificações. Por exemplo, um ideograma chinês tem nenhum mapeamento razoável para a página de código 1252. Nesse caso, é usada uma cadeia de caracteres de substituição. Por padrão, essa cadeia de caracteres é apenas um PONTO DE INTERROGAÇÃO (U+003F).

O exemplo a seguir usa a página de código 1252 (a página de código do Windows para idiomas da Europa Ocidental) para ilustrar o mapeamento de melhor ajuste e suas desvantagens. O método [Encoding.GetEncoding(Int32](xref:System.Text.Encoding.GetEncoding(System.Int32)) é usado para recuperar um objeto de codificação para a página de código 1252. Por padrão, ele usa um mapeamento de melhor ajuste para caracteres Unicode aos quais ele não dá suporte. O exemplo cria uma instância de uma cadeia de caracteres que contém três caracteres não ASCII – LETRA MAIÚSCULA LATINA S CIRCULADA (U+24C8), CINCO SOBRESCRITO (U+2075) e INFINITO (U+221E) – separados por espaços. Como mostra a saída de exemplo, quando a cadeia de caracteres é codificada, os três caracteres originais sem espaço são substituídos pelo PONTO DE INTERROGAÇÃO (U+003F), DÍGITO CINCO (U+0035) e DÍGITO OITO (U+0038). DÍGITO OITO é um substituto especialmente ruim para o caractere INFINITO sem suporte e o PONTO DE INTERROGAÇÃO indica que nenhum mapeamento estava disponível para o caractere original.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

O mapeamento de melhor ajuste é o comportamento padrão para um objeto [Encoding](xref:System.Text.Encoding) que codifica dados Unicode em dados da página de código e há aplicativos herdados que se baseiam nesse comportamento. No entanto, a maioria dos novos aplicativos devem evitar o comportamento de melhor ajuste por motivos de segurança. Por exemplo, os aplicativos não devem colocar um nome de domínio por meio de uma codificação de melhor ajuste.

> [!Note]
> Você também pode implementar um mapeamento de fallback de melhor ajuste personalizado para uma codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).
 
Se o fallback de melhor ajuste for o padrão para um objeto de codificação, você poderá escolher outra estratégia de fallback quando você recuperar um objeto [Encoding](xref:System.Text.Encoding) chamando a sobrecarga [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) ou [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). A seção a seguir inclui um exemplo que substitui cada caractere que não pode ser mapeado para a página de código 1252 com um asterisco (\*).

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a>Fallback de substituição

Quando um caractere não tem uma correspondência exata do esquema de destino, mas não há nenhum caractere apropriado para o qual ele pode ser mapeado, o aplicativo pode especificar um caractere ou uma cadeia de caracteres de substituição. Esse é o comportamento padrão para o decodificador de Unicode, que substitui qualquer sequência de dois bytes que ele não pode decodificar por REPLACEMENT_CHARACTER (U+FFFD). Também é o comportamento padrão da classe [ASCIIEncoding](xref:System.Text.ASCIIEncoding), que substitui cada caractere que ela não pode codificar ou decodificar por um ponto de interrogação. O exemplo a seguir ilustra a substituição de caracteres para a cadeia de caracteres Unicode do exemplo anterior. Como mostra a saída, cada caractere que não puder ser decodificado em um valor de bytes ASCII é substituído por 0x3F, que é o código ASCII para um ponto de interrogação.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

O .NET inclui as classes [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) e [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback), que substituem uma cadeia de caracteres de substituição se um caractere não mapear exatamente em uma operação de codificação ou decodificação. Por padrão, essa cadeia de caracteres de substituição é um ponto de interrogação, mas você pode chamar uma sobrecarga do construtor de classes para escolher uma cadeia de caracteres diferente. Normalmente, a cadeia de caracteres de substituição é um único caractere, embora isso não seja um requisito. O exemplo a seguir altera o comportamento do codificador da página de código 1252 criando uma instância de um objeto [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) que usa um asterisco (\*) como uma cadeia de caracteres de substituição.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> Você também pode implementar uma classe de substituição para uma codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).
 
Além de PONTO DE INTERROGAÇÃO (U+003F), o CARACTERE DE SUBSTITUIÇÃO Unicode (U+FFFD) normalmente é usado como uma cadeia de caracteres de substituição, especialmente ao decodificar sequências de bytes que não podem ser convertidas com êxito em caracteres Unicode. No entanto, você está livre para escolher qualquer cadeia de caracteres de substituição e ela pode conter vários caracteres.

### <a name="exception-fallback"></a>Fallback de exceção

Em vez de oferecer um fallback de melhor ajuste ou uma cadeia de caracteres de substituição, um codificador pode lançar uma [EncoderFallbackException](xref:System.Text.EncoderFallbackException) se não for possível codificar um conjunto de caracteres e um decodificador pode lançar uma [DecoderFallbackException](xref:System.Text.DecoderFallbackException) se não for possível decodificar uma matriz de bytes. Para lançar uma exceção nas operações de codificação e decodificação, você deve fornecer um objeto [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e um objeto [DecoderFallbackException](xref:System.Text.DecoderFallbackException), respectivamente, para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). O exemplo a seguir ilustra a o fallback de exceção com a classe ASCIIEncoding.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> Você também pode implementar um manipulador de exceção personalizado para uma operação de codificação. Para obter mais informações, consulte a seção [Implementando uma estratégia de fallback personalizada](#implementing-a-custom-fallback-strategy).
 
Os objetos [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fornecem as seguintes informações sobre a condição que causou a exceção: 

* O objeto [EncoderFallbackException](xref:System.Text.EncoderFallbackException) inclui um método [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate), que indica se o caractere ou caracteres que não podem ser codificados representam um par alternativo desconhecido (nesse caso, o método retorna `true`) ou um único caractere desconhecido (nesse caso, o método retorna `false`). Os caracteres do par alternativo estão disponíveis nas propriedades [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) e [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow). O único caractere desconhecido está disponível na propriedade [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown). A propriedade [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) indica a posição na cadeia de caracteres na qual o primeiro caractere que não pôde ser codificado foi encontrado.

* O objeto [DecoderFallbackException](xref:System.Text.DecoderFallbackException) inclui uma propriedade [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) que retorna uma matriz de bytes que não pode ser decodificada. A propriedade [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) indica a posição inicial dos bytes desconhecidos.

Embora os objetos [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) forneçam informações de diagnóstico adequadas sobre a exceção, eles não fornecem acesso ao buffer de codificação ou decodificação. Portanto, eles não permitem que dados inválidos sejam substituídos ou corrigidos dentro do método de codificação ou de decodificação.

## <a name="implementing-a-custom-fallback-strategy"></a>Implementando uma estratégia de fallback personalizada

Além do mapeamento de melhor ajuste implementado internamente por páginas de código, o .NET inclui as seguintes classes para implementar uma estratégia de fallback:

* Use [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) e [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para substituir caracteres em operações de codificação.

* Use [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para substituir caracteres em operações de decodificação.

* Use [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) e [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para lançar um [EncoderFallbackException](xref:System.Text.EncoderFallbackException) quando um caractere não puder ser codificado.

* Use [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para lançar um [DecoderFallbackException](xref:System.Text.DecoderFallbackException) quando um caractere não puder ser decodificado.

Além disso, você pode implementar uma solução personalizada que usa o fallback de melhor ajuste, fallback de substituição ou fallback de exceção seguindo estas etapas: 

1. Derive uma classe de [EncoderFallback](xref:System.Text.EncoderFallback) para operações de codificação e de [DecoderFallback](xref:System.Text.DecoderFallback) para operações de decodificação.

2. Derive uma classe de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para operações de codificação e de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para operações de decodificação.

3. Para o fallback de exceção, se as classes [EncoderFallbackException](xref:System.Text.EncoderFallbackException) e [DecoderFallbackException](xref:System.Text.DecoderFallbackException) predefinidas não atenderem às suas necessidades, derive uma classe de um objeto de exceção como [Exception](xref:System.Exception) ou [ArgumentException](xref:System.ArgumentException).

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Derivando de EncoderFallback ou DecoderFallback

Para implementar uma solução de fallback personalizada, você deverá criar uma classe herdada de [EncoderFallback](xref:System.Text.EncoderFallback) para operações de codificação e de [DecoderFallback](xref:System.Text.DecoderFallback) para operações de decodificação. As instâncias dessas classes são passadas para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) e funcionam como intermediário entre a classe de codificação e a implementação do fallback.

Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:

* A propriedade [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) ou [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount), que retorna o número máximo possível de caracteres que o fallback de melhor ajuste, de substituição ou de exceção pode retornar para substituir um único caractere. Para um fallback de exceção personalizado, seu valor é zero. 

* O método [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) ou [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer), que retorna sua implementação [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) ou [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) personalizada. O método é chamado pelo codificador quando ele encontra o primeiro caractere que ele não consegue codificar com êxito ou pelo decodificador quando ele encontra o primeiro byte que ele não consegue decodificar com êxito.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Derivando de EncoderFallbackBuffer ou DecoderFallbackBuffer

Para implementar uma solução de fallback personalizada, você também deverá criar uma classe herdada de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) para operações de codificação e de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) para operações de decodificação. As instâncias dessas classes são retornadas pelo método `CreateFallbackBuffer` das classes [EncoderFallback](xref:System.Text.EncoderFallback) e [DecoderFallback](xref:System.Text.DecoderFallback). O método [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) é chamado pelo codificador quando ele encontra o primeiro caractere que ele não consegue codificar e o método [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) é chamado pelo decodificador quando ele encontra um ou mais bytes que ele não consegue decodificar. As classes [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) fornecem a implementação de fallback. Cada instância representa um buffer que contém os caracteres de fallback que substituirão o caractere que não pode ser codificado ou a sequência de bytes que não pode ser decodificada.

Quando você cria uma solução de fallback personalizada para um codificador ou um decodificador, você deve implementar os seguintes membros:

* O método [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) ou [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)). [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) é chamado pelo codificador para fornecer ao buffer de fallback informações sobre o caractere que ele não consegue codificar. Como o caractere a ser codificado pode ser um par alternativo, esse método está sobrecarregado. Uma sobrecarga é passada para o caractere a ser codificado e para o seu índice na cadeia de caracteres. A segunda sobrecarga é passada para os substitutos altos e baixos juntamente com seu índice na cadeia de caracteres. O método [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) é chamado pelo decodificador para fornecer ao buffer de fallback informações sobre os bytes que ele não consegue decodificar. Esse método recebe uma matriz de bytes que ele não consegue decodificar, juntamente com o índice do primeiro byte. O método de fallback deverá retornar `true` se o buffer de fallback conseguir fornecer caracteres de melhor ajuste ou de substituição; caso contrário, ele deverá retornar `false`. Para um fallback de exceção, o método de fallback deve lançar uma exceção.

* O método [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) ou [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar), chamado repetidamente pelo codificador ou decodificador para obter o próximo caractere do buffer de fallback. Quando todos os caracteres de fallback tiverem sido retornados, o método deverá retornar U+0000. 

* A propriedade [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) ou [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining), que retorna o número de caracteres restantes no buffer de fallback.

* O método [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) ou [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious), que move a posição atual no buffer de fallback para o caractere anterior.

* O método [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) ou [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset), que reinicializa o buffer de fallback.

Se a implementação de fallback for um fallback de melhor ajuste ou de substituição, as classes derivadas de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) e [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) também mantêm dois campos de instância privados: o número exato de caracteres no buffer e o índice do próximo caractere no buffer a ser retornado.

### <a name="an-encoderfallback-example"></a>Um exemplo de EncoderFallback

Um exemplo anterior usava o fallback de substituição para substituir caracteres Unicode que não correspondiam aos caracteres ASCII por um asterisco (\*). O exemplo a seguir usa uma implementação de fallback de melhor ajuste personalizada em vez de fornecer um melhor mapeamento de caracteres não ASCII.

O código a seguir define uma classe chamada `CustomMapper` derivada de [EncoderFallback](xref:System.Text.EncoderFallback) para lidar com o mapeamento de melhor ajuste de caracteres não ASCII. Seu método `CreateFallbackBuffer` retorna um objeto `CustomMapperFallbackBuffer`, que fornece a implementação do [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer). A classe `CustomMapper` usa um objeto [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) para armazenar os mapeamentos de caracteres Unicode sem suporte (o valor da chave) e seus caracteres de 8 bits correspondentes (armazenados em dois bytes consecutivos em um inteiro de 64 bits). Para disponibilizar esse mapeamento ao buffer de fallback, a instância `CustomMapper` é passada como um parâmetro para o construtor de classe `CustomMapperFallbackBuffer`. Como o mapeamento mais longo é a cadeia de caracteres "INF" para o caractere Unicode U+221E, a propriedade `MaxCharCount` retorna 3. 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

O código a seguir define a classe `CustomMapperFallbackBuffer`, derivada de [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer). O dicionário que contém mapeamentos de melhor ajuste e definido na instância `CustomMapper` está disponível no seu construtor de classe. Seu método `Fallback` retornará `true` se qualquer um dos caracteres Unicode que o codificador ASCII não conseguir codificar forem definidos no dicionário de mapeamento; caso contrário, retornará `false`. Para cada fallback, a variável `count` privada indica o número de caracteres que continuam sendo retornados e a variável `index` privada indica a posição no buffer de cadeia de caracteres, `charsToReturn`, do próximo caractere a ser retornado. 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

O código a seguir cria uma instância do objeto `CustomMapper` e passa uma instância dele para o método [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). A saída indica que a implementação de fallback de melhor ajuste lida com êxito com os três caracteres não ASCII na cadeia de caracteres original.

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a>Consulte também

[System.Text.Encoder](xref:System.Text.Encoder)

[System.Text.EncoderFallback](xref:System.Text.EncoderFallback)

[System.Text.Decoder](xref:System.Text.Decoder)

[System.Text.DecoderFallback](xref:System.Text.DecoderFallback)

[System.Text.Encoding](xref:System.Text.Encoding)







<!--HONumber=Nov16_HO3-->


