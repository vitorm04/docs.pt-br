---
title: "Cadeias de caracteres de formato numérico padrão"
description: "Cadeias de caracteres de formato numérico padrão"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 285faf73-466a-4af0-8eba-7e509958f240
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 4887a55690e47f7867cee28ab9b9fe258b208e54

---

# <a name="standard-numeric-format-strings"></a>Cadeias de caracteres de formato numérico padrão

As cadeias de caracteres de formato numérico padrão são usadas para formatar tipos numéricos comuns. Uma cadeia de caracteres de formato numérico padrão assume o formato **A**_xx_, em que: 

* **A** é um caractere alfabético único chamado *especificador de formato*. Qualquer cadeia de caracteres de formato numérico que contém mais de um caractere alfabético, incluindo espaços em branco, é interpretada como uma cadeia de caracteres de formato numérico personalizado. Para obter mais informações, consulte [Cadeias de caracteres de formato numérico personalizado](custom-numeric.md). 

* *xx* é um inteiro opcional chamado *especificador de precisão*. O especificador de precisão varia de 0 a 99 e afeta o número de dígitos no resultado. Observe que o especificador de precisão controla o número de dígitos na representação da cadeia de caracteres de um número. Ele não arredonda o número em si. Para executar uma operação de arredondamento, use os métodos [Math.Ceiling](xref:System.Math), [Math.Floor](xref:System.Math) ou [Math.Round](xref:System.Math). 

Quando o *especificador de precisão* controla o número de dígitos fracionários na cadeia de caracteres de resultado, as cadeias de caracteres de resultado refletem números que são arredondados para cima (ou seja, usando o [MidpointRounding.AwayFromZero](xref:System.MidpointRounding.AwayFromZero)). 

> [!NOTE]
> O especificador de precisão determina o número de dígitos na cadeia de caracteres de resultado. Para acrescentar espaços à direita ou à esquerda em uma cadeia de caracteres de resultado, use o recurso [formatação de composição](composite-format.md) e defina um *componente de alinhamento* no item de formato. 

As cadeias de caracteres de formato numérico padrão têm suporte em algumas sobrecargas do método `ToString` de todos os tipos numéricos. Por exemplo, você pode fornecer uma cadeia de caracteres de formato numérico aos métodos [ToString(String)](xref:System.Int32.ToString(System.String)) e [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) do tipo [Int32](xref:System.Int32). As cadeias de caracteres de formato numérico padrão também têm suporte no recurso de [formatação de composição](composite-format.md) do .NET, o qual é usado por alguns métodos `Write` e `WriteLine` das classes [Console](xref:System.Console) e [StreamWriter](xref:System.IO.StreamWriter), o método [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) e o método [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)). O recurso de formato de composição permite a inclusão da representação da cadeia de caracteres de vários itens de dados em uma única cadeia de caracteres, para especificar a largura do campo e alinhar os números em um campo. Para obter mais informações, veja [Formatação de composição](composite-format.md). 

A tabela a seguir descreve os especificadores de formato numérico padrão e exibe exemplos de saídas produzidas por cada especificador de formato. Consulte a seção [Notas](#notes) para obter informações adicionais sobre como usar cadeias de caracteres de formato numérico padrão e a seção [Exemplo](#example) para obter uma ilustração abrangente de seu uso.

|Especificador de formato|Nome|Descrição|Exemplos|  
|----------------------|----------|-----------------|--------------|  
|"C" ou "c"|Moeda|Resultado: um valor de moeda.<br /><br /> Compatível com: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de casas decimais.<br /><br /> Especificador de precisão padrão: definido por [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits).<br /><br /> |123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|"D" ou "d"|Decimal|Resultado: dígitos inteiros com sinal negativo opcional.<br /><br /> Compatível com: somente tipos integrais.<br /><br /> Especificador de precisão: número mínimo de dígitos.<br /><br /> Especificador de precisão padrão: número mínimo de dígitos necessários.<br /><br /> |1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|"E" ou "e"|Exponencial (científica)|Resultado: notação Exponencial.<br /><br /> Compatível com: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de casas decimais.<br /><br /> Especificador de precisão padrão: 6.<br /><br /> |1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1,05E+003|  
|"F" ou "f"|Ponto fixo|Resultado: dígitos integrais e decimais com sinal negativo opcional.<br /><br /> Compatível com: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de casas decimais.<br /><br /> Especificador de precisão padrão: definido por [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits).<br /><br /> |1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|  
|"G" ou "g"|Geral|Resultado: a mais compacta entre notação de ponto fixo ou científica.<br /><br /> Suporte por: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de dígitos significativos.<br /><br /> Especificador de precisão padrão: depende do tipo numérico.<br /><br /> |-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|"N" ou "n"|Número|Resultado: dígitos integrais e decimais, separadores de grupo e um separador decimal com sinal negativo opcional.<br /><br /> Compatível com: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de casas decimais desejadas.<br /><br /> Especificador de precisão padrão: definido por [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits).<br /><br /> |1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|  
|"P" ou "p"|Porcentagem|Resultado: número multiplicado por 100 e exibido com um sinal de porcentagem.<br /><br /> Compatível com: todos os tipos numéricos.<br /><br /> Especificador de precisão: número de casas decimais desejadas.<br /><br /> Especificador de precisão padrão: definido por  [NumberFormatInfo.PercentDecimalDigits](assetId:///P:System.Globalization.NumberFormatInfo.PercentDecimalDigits?qualifyHint=True&autoUpgrade=True).<br /><br /> |1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|  
|"R" ou "r"|Ida e volta|Resultado: uma cadeia de caracteres que pode ir e voltar para um número idêntico.<br /><br /> Suporte por: [Single](xref:System.Single), [Double](xref:System.Double) e [BigInteger](xref:System.Numerics.BigInteger).<br /><br /> Especificador de precisão: ignorado.<br /><br /> |123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|"X" ou "x"|Hexadecimal|Resultado: uma cadeia de caracteres hexadecimal.<br /><br /> Compatível com: somente tipos integrais.<br /><br /> Especificador de precisão: número de dígitos na cadeia de caracteres de resultado.<br /><br /> |255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|Qualquer outro caractere único|Especificador desconhecido|Resultado: gera um [FormatException](xref:System.FormatException) em tempo de execução.|| 

## <a name="using-standard-numeric-format-strings"></a>Usando cadeias de caracteres de formato numérico padrão

Uma cadeia de caracteres de formato numérico padrão pode ser usada para definir a formatação de um valor numérico em uma de duas formas:

* Ela pode ser passada para uma sobrecarga do método `ToString` que tem um parâmetro *format*. O exemplo a seguir formata um valor numérico como uma cadeia de caracteres de moeda na cultura atual (nesse caso, en-US). 

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine(value.ToString("C2"));
  // Displays $123.46
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine(value.ToString("C2"))         
  ' Displays $123.46
  ```
  
* Ela pode ser fornecida como o argumento *formatString* em um item de formato usado com métodos como [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), [Console.WriteLine](xref:System.Console.WriteLine) e [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)). Para obter mais informações, veja [Formatação de composição](composite-format.md). O exemplo a seguir usa um item de formato para inserir um valor de moeda em uma cadeia de caracteres.

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine("Your account balance is {0:C2}.", value);
  // Displays "Your account balance is $123.46."
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine("Your account balance is {0:C2}.", value)
  ' Displays "Your account balance is $123.46."
  ```
  
  Opcionalmente, um argumento de alinhamento pode ser fornecido para especificar a largura do campo numérico e se o valor é alinhado à direita ou à esquerda. O exemplo a seguir alinha à esquerda um valor de moeda em um campo de 28 caracteres e alinha à direita um valor de moeda em um campo de 14 caracteres.
  
  ```csharp
  decimal[] amounts = { 16305.32m, 18794.16m };
  Console.WriteLine("   Beginning Balance           Ending Balance");
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts[0], amounts[1]);
  // Displays:
  //        Beginning Balance           Ending Balance
  //        $16,305.32                      $18,794.16
  ```

  ```vb
  Dim amounts() As Decimal = { 16305.32d, 18794.16d }
  Console.WriteLine("   Beginning Balance           Ending Balance")
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts(0), amounts(1))
  ' Displays:
  '        Beginning Balance           Ending Balance
  '        $16,305.32                      $18,794.16
  ```
  
As seções a seguir fornecem informações detalhadas sobre cada uma das cadeias de caracteres de formato numérico padrão.

## <a name="the-currency-c-format-specifier"></a>O especificador de formato de moeda ("C")

O especificador de formato "C" (ou moeda) converte um número em uma cadeia de caracteres que representa um valor de moeda. O especificador de precisão indica o número desejado de casas decimais na cadeia de caracteres resultante. Se o especificador de precisão for omitido, a precisão padrão será definida pela propriedade [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits).

Se o valor a ser formatado tem mais do que o número especificado ou padrão de casas decimais, o valor fracionário é arredondado na cadeia de caracteres de resultado. Se o valor à direita do número de casas decimais especificadas for 5 ou mais, o último dígito da cadeia de caracteres do resultado será arredondado para cima.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) | Define o posicionamento do símbolo de moeda para valores positivos.
[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) | Define o posicionamento do símbolo da moeda para valores negativos e especifica se o sinal de negativo é representado por parênteses ou pela propriedade [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign).
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define o sinal de negativo usado se [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) indicar que parênteses não são usados. 
[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) | Define o símbolo de moeda.
[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) | Define o número padrão de dígitos decimais em um valor de moeda. Esse valor pode ser substituído usando-se o especificador de precisão.
[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) | Define a cadeia de caracteres que separa dígitos decimais e integrais.
[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) | Define a cadeia de caracteres que separa grupos de números integrais. 
[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) | Define o número de dígitos inteiros que aparecem em um grupo.

O exemplo a seguir formata um valor [Double](xref:System.Double) com o especificador de formato de moeda. 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", 
                  CultureInfo.CreateSpecificCulture("da-DK")));
// The example displays the following output on a system whose
// current culture is English (United States):
//       $12,345.68
//       $12,345.679
//       kr 12.345,679
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", _
                  CultureInfo.CreateSpecificCulture("da-DK")))
' The example displays the following output on a system whose
' current culture is English (United States):
'       $12,345.68
'       $12,345.679
'       kr 12.345,679
```

## <a name="the-decimal-d-format-specifier"></a>O especificador de formato decimal ("D")

O especificador de formato “D” (ou decimal) converte um número em uma cadeia de caracteres de dígitos decimais (0-9), prefixados por um sinal de negativo se o número for negativo. Esse formato é compatível apenas com tipos integrais.

O especificador de precisão indica o número mínimo de dígitos desejados na cadeia de caracteres resultante. Se necessário, o número é preenchido com zeros à esquerda para produzir o número de dígitos fornecido pelo especificador de precisão. Quando nenhum especificador de precisão é especificado, o padrão é o valor mínimo necessário para representar o inteiro sem zeros à esquerda.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. Conforme mostrado na tabela a seguir, uma única propriedade afeta a formatação da cadeia de caracteres de resultado. 

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo. 

O exemplo a seguir formata um valor [Int32](xref:System.Int32) com o especificador de formato decimal.

```csharp
int value; 

value = 12345;
Console.WriteLine(value.ToString("D"));
// Displays 12345
Console.WriteLine(value.ToString("D8"));
// Displays 00012345

value = -12345;
Console.WriteLine(value.ToString("D"));
// Displays -12345
Console.WriteLine(value.ToString("D8"));
// Displays -00012345
```

```vb
Dim value As Integer 

value = 12345
Console.WriteLine(value.ToString("D"))
' Displays 12345   
Console.WriteLine(value.ToString("D8"))
' Displays 00012345

value = -12345
Console.WriteLine(value.ToString("D"))
' Displays -12345
Console.WriteLine(value.ToString("D8"))
' Displays -00012345
```

## <a name="the-exponential-e-format-specifier"></a>O especificador de formato exponencial ("E")

O especificador do formato do exponencial ("E") converte um número em uma cadeia de caracteres no formato "-d.ddd…E+ddd" ou "-d.ddd…e+ddd", em que cada 'd' indica um dígito (0-9). A cadeia de caracteres é iniciada com um sinal de negativo se o número é negativo. Exatamente um dígito sempre precede o ponto decimal. 

O especificador de precisão indica o número desejado de dígitos após o ponto decimal. Quando o especificador de precisão é omitido, um padrão de seis dígitos após o ponto decimal é usado. 

A caixa do especificador de formato indica se o expoente é prefixado com um "E" ou um "e". O expoente sempre consistem em um sinal de positivo ou negativo e um mínimo de três dígitos. O expoente é preenchido com zeros para atender a esse mínimo, se necessário.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que o número é negativo para o coeficiente e o expoente. 
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Define a cadeia de caracteres que separa o dígito integral dos dígitos decimais no coeficiente.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Define a cadeia de caracteres que indica que um expoente é positivo.

O exemplo a seguir formata um valor [Double](xref:System.Double) com o especificador de formato exponencial. 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture));
// Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture));
// Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture));
// Displays 1.2346e+004

Console.WriteLine(value.ToString("E", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 1,234568E+004
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture))
' Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture))
' Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture))
' Displays 1.2346e+004

Console.WriteLine(value.ToString("E", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 1,234568E+004
```

## <a name="the-fixed-point-f-format-specifier"></a>O especificador de formato de ponto fixo ("F")

O especificador de formato de ponto fixo ("F") converte um número em uma cadeia de caracteres no formato "-ddd.ddd…" em que cada "d" indica um dígito (0-9). A cadeia de caracteres é iniciada com um sinal de negativo se o número é negativo. 

O especificador de precisão indica o número de casas decimais desejadas. Se o especificador de precisão for omitido, a propriedade [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) atual fornece a precisão numérica.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres de resultado.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Define a cadeia de caracteres que separa dígitos integrais de dígitos decimais.
[NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | Define o número padrão de dígitos decimais. Esse valor pode ser substituído usando-se o especificador de precisão.

O exemplo a seguir formata um valor [Double](xref:System.Double) e um valor [Int32](xref:System.Int32) com o especificador de formato de ponto fixo.

```csharp
int integerNumber;
integerNumber = 17843;
Console.WriteLine(integerNumber.ToString("F", 
                  CultureInfo.InvariantCulture));
// Displays 17843.00

integerNumber = -29541;
Console.WriteLine(integerNumber.ToString("F3", 
                  CultureInfo.InvariantCulture));
// Displays -29541.000

double doubleNumber;
doubleNumber = 18934.1879;
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture));
// Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture));
// Displays 18934

doubleNumber = -1898300.1987;
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture));  
// Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays -1898300,199 
```

```vb
Dim integerNumber As Integer
integerNumber = 17843
Console.WriteLine(integerNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 17843.00

integerNumber = -29541
Console.WriteLine(integerNumber.ToString("F3", CultureInfo.InvariantCulture))
' Displays -29541.000

Dim doubleNumber As Double
doubleNumber = 18934.1879
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture))
' Displays 18934

doubleNumber = -1898300.1987
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture))  
' Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", _ 
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays -1898300,199                        
```

## <a name="the-general-g-format-specifier"></a>O especificador de formato geral ("G")

O especificador de formato geral ("G") converte um número para a notação mais compacta entre ponto fixo ou científica, dependendo do tipo do número e se um especificador de precisão está presente. O especificador de precisão define o número máximo de dígitos significativos que podem aparecer na cadeia de caracteres de resultado. Quando o especificador de precisão é omitido ou zero, o tipo do número determina a precisão padrão, conforme indicado na tabela a seguir. 

Tipo numérico | Precisão padrão
------------ | -----------------
[Byte](xref:System.Byte) ou [SByte](xref:System.SByte) | 3 dígitos
[Int16](xref:System.Int16) ou [UInt16](xref:System.UInt16) | 5 dígitos
[Int32](xref:System.Int32) ou [UInt32](xref:System.UInt32) | 10 dígitos
[Int64](xref:System.Int64) | 19 dígitos
[UInt64](xref:System.UInt64) | 20 dígitos
[BigInteger](xref:System.Numerics.BigInteger) | Ilimitado (igual a "R")
[Simples](xref:System.Single) | 7 dígitos
[Duplo](xref:System.Double) | 15 dígitos
[Decimal](xref:System.Decimal) | 29 dígitos

A notação de ponto fixo é usada se o expoente que resultaria ao expressar o número na notação científica é maior do que -5 e menor que o especificador de precisão; caso contrário, a notação científica é usada. Se necessário, o resultado contém um ponto decimal, e os zeros à direita após o ponto decimal são omitidos. Se o especificador de precisão estiver presente e o número de dígitos significativos no resultado exceder a precisão especificada, o excesso de dígitos à direita será removido por arredondamento. 

No entanto, se o número for um [Decimal](xref:System.Decimal) e o especificador de precisão for omitido, a notação de ponto fixo será sempre usada e os zeros à direita serão preservados.

Se a notação científica for usada, o expoente no resultado será prefixado com "E" se o especificador de formato for "G" ou "e" se o especificador de formato for "g". O expoente contém um mínimo de dois dígitos. Isso difere do formato de notação científica que é gerado pelo especificador de formato exponencial, o qual inclui um mínimo de três dígitos no expoente.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres de resultado.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Define a cadeia de caracteres que separa dígitos integrais de dígitos decimais.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Define a cadeia de caracteres que indica que um expoente é positivo. 

O exemplo a seguir formata valores de ponto flutuante variados com o especificador de formato geral.

```csharp
double number;

number = 12345.6789;      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays  12345.6789
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture));
// Displays 12345.68 

number = .0000023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 2.3E-06       
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 2,3E-06

number = .0023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 0.0023

number = 1234;
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture));
// Displays 1.2E+03

number = Math.PI;
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture));
// Displays 3.1416    
```

```vb
Dim number As Double

number = 12345.6789      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays  12345.6789
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture))
' Displays 12345.68 

number = .0000023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 2.3E-06       
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 2,3E-06

number = .0023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 0.0023

number = 1234
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture))
' Displays 1.2E+03

number = Math.Pi
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture))
' Displays 3.1416
```

## <a name="the-numeric-n-format-specifier"></a>O especificador de formato numérico ("N")

O especificador de formato numérico ("N") converte um número em uma cadeia de caracteres no formato "-d,ddd,ddd.ddd…", em que "-" indica um símbolo de número negativo, se necessário, "d" indica um dígito (0-9), "," indica um separador de grupos de número e "." indica um símbolo de ponto decimal. O especificador de precisão indica o número desejado de dígitos após o ponto decimal. Se o especificador de precisão for omitido, o número de casas decimais será definido pela propriedade [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) atual.

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres de resultado.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo.
[NumberNegativePattern](xref:System.Globalization.NumberFormatInfo.NumberNegativePattern) | Define o formato dos valores negativos e especifica se o sinal de negativo é representado por parênteses ou pela propriedade [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign).
[NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) | Define o número total de dígitos integrais que aparecem entre os separadores de grupo.
[NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) | Define a cadeia de caracteres que separa grupos de números integrais.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Define a cadeia de caracteres que separa dígitos integrais de dígitos decimais.
[NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | Define o número padrão de dígitos decimais. Esse valor pode ser substituído usando um especificador de precisão.

O exemplo a seguir formata valores de ponto flutuante variados com o especificador de formato numérico.

```csharp
double dblValue = -12445.6789;
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture));
// Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", 
                  CultureInfo.CreateSpecificCulture("sv-SE")));
// Displays -12 445,7

int intValue = 123456789;
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture));
// Displays 123,456,789.0 
```

```vb
Dim dblValue As Double = -12445.6789
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture))
' Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", _
                  CultureInfo.CreateSpecificCulture("sv-SE")))
' Displays -12 445,7

Dim intValue As Integer = 123456789
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture))
' Displays 123,456,789.0 
```

## <a name="the-percent-p-format-specifier"></a>O especificador de formato de porcentagem ("P")

O especificador de formato de porcentagem (“P”) multiplica um número por 100 e o converte em uma cadeia de caracteres que representa uma porcentagem. O especificador de precisão indica o número de casas decimais desejadas. Se o especificador de precisão for omitido, a precisão numérica padrão fornecida pela propriedade [PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) atual será usada.

A tabela a seguir lista as propriedades do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres retornada.

Propriedade umberFormatInfo | Descrição
------------------------- | -----------
[PercentPositivePattern](xref:System.Globalization.NumberFormatInfo.PercentPositivePattern) | Define o posicionamento do símbolo de porcentagem para valores positivos.
[PercentNegativePattern](xref:System.Globalization.NumberFormatInfo.PercentNegativePattern) | 
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo.
[PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) | Define o símbolo de porcentagem.
[PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) | Define o número padrão de dígitos decimais em um valor percentual. Esse valor pode ser substituído usando-se o especificador de precisão.
[PercentDecimalSeparator](xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator) | Define a cadeia de caracteres que separa dígitos decimais e integrais.
[PercentGroupSeparator](xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator) | Define a cadeia de caracteres que separa grupos de números integrais. 
[PercentGroupSizes](xref:System.Globalization.NumberFormatInfo.PercentGroupSizes) | Define o número de dígitos inteiros que aparecem em um grupo.

O exemplo a seguir formata valores de ponto flutuante variados com o especificador de formato de porcentagem.

```csharp
double number = .2468013;
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture));
// Displays 24.68 %
Console.WriteLine(number.ToString("P", 
                  CultureInfo.CreateSpecificCulture("hr-HR")));
// Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture));
// Displays 24.7 %
```

```vb
Dim number As Double = .2468013
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture))
' Displays 24.68 %
Console.WriteLine(number.ToString("P", _
                  CultureInfo.CreateSpecificCulture("hr-HR")))
' Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture))
' Displays 24.7 %
```

## <a name="the-round-trip-r-format-specifier"></a>O especificador de formato de ida e volta ("R")

O especificador de formato de ida e volta ("R") é usado para garantir que um valor numérico convertido em uma cadeia de caracteres será analisado de volta para o mesmo valor numérico. Esse formato tem suporte apenas para os tipos [Single](xref:System.Single), [Double](xref:System.Double) e [BigInteger](xref:System.Numerics.BigInteger). 

Quando um valor [BigInteger](xref:System.Numerics.BigInteger) é formatado usando esse especificador, sua representação de cadeia de caracteres contém todos os dígitos significativos no valor [BigInteger](xref:System.Numerics.BigInteger). Quando um valor [Single](xref:System.Single) ou [Double](xref:System.Double) é formatado usando esse especificador, ele é testado primeiro usando o formato geral, com 15 dígitos de precisão para um [Double](xref:System.Double) e 7 dígitos de precisão para um [Single](xref:System.Single). Se o valor é analisado com êxito de volta para o mesmo valor numérico, ele é formatado usando o especificador de formato geral. Se o valor não for analisado com êxito de volta para o mesmo valor numérico, ele será formatado com 17 dígitos de precisão para um [Double](xref:System.Double) e 9 dígitos de precisão para um [Single](xref:System.Single). 

Embora você possa incluir um especificador de precisão, ele será ignorado. Idas e voltas têm precedência sobre a precisão quando esse especificador é usado. 

A cadeia de caracteres de resultado é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. A tabela a seguir lista as propriedades [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controlam a formatação da cadeia de caracteres de resultado.

Propriedade NumberFormatInfo | Descrição
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Define a cadeia de caracteres que indica que um número é negativo.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Define a cadeia de caracteres que separa dígitos integrais de dígitos decimais.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Define a cadeia de caracteres que indica que um expoente é positivo.

 O exemplo a seguir formata valores [Double](xref:System.Double) com o especificador de formato de ida e volta.

```csharp
double value;

value = Math.PI;
Console.WriteLine(value.ToString("r"));
// Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 3,1415926535897931
value = 1.623e-21;
Console.WriteLine(value.ToString("r"));
// Displays 1.623E-21
```

```vb
Dim value As Double

value = Math.Pi
Console.WriteLine(value.ToString("r"))
' Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 3,1415926535897931
value = 1.623e-21
Console.WriteLine(value.ToString("r"))
' Displays 1.623E-21
```

## <a name="the-hexadecimal-x-format-specifier"></a>O especificador de formato hexadecimal ("X")

O especificador de formato hexadecimal ("X") converte um número em uma cadeia de caracteres de dígitos hexadecimais. A caixa do especificador de formato indica se caracteres maiúsculos ou minúsculos devem ser usados para os dígitos hexadecimais maiores que 9. Por exemplo, use "X" para produzir "ABCDEF" e "x" para produzir "abcdef". Esse formato é compatível apenas com tipos integrais.

O especificador de precisão indica o número mínimo de dígitos desejados na cadeia de caracteres resultante. Se necessário, o número é preenchido com zeros à esquerda para produzir o número de dígitos fornecido pelo especificador de precisão.

A cadeia de caracteres do resultado não é afetada pelas informações de formatação do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual. 

O exemplo a seguir formata valores [Int32](xref:System.Int32) com o especificador de formato hexadecimal.

```csharp
int value; 

value = 0x2045e;
Console.WriteLine(value.ToString("x"));
// Displays 2045e
Console.WriteLine(value.ToString("X"));
// Displays 2045E
Console.WriteLine(value.ToString("X8"));
// Displays 0002045E

value = 123456789;
Console.WriteLine(value.ToString("X"));
// Displays 75BCD15
Console.WriteLine(value.ToString("X2"));
// Displays 75BCD15
```

```vb
Dim value As Integer 

value = &h2045e
Console.WriteLine(value.ToString("x"))
' Displays 2045e
Console.WriteLine(value.ToString("X"))
' Displays 2045E
Console.WriteLine(value.ToString("X8"))
' Displays 0002045E

value = 123456789
Console.WriteLine(value.ToString("X"))
' Displays 75BCD15
Console.WriteLine(value.ToString("X2"))
' Displays 75BCD15
```

## <a name="notes"></a>Anotações

### <a name="numberformatinfo-properties"></a>Propriedades de NumberFormatInfo

A formatação é influenciada pelas propriedades do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual, o qual é fornecido implicitamente pela cultura do thread atual ou explicitamente pelo parâmetro [IFormatProvider](xref:System.IFormatProvider) do método que invoca a formatação. Especifique um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) ou [CultureInfo](xref:System.Globalization.CultureInfo) para esse parâmetro. 

### <a name="integral-and-floating-point-numeric-types"></a>Tipos numéricos integrais e de ponto flutuante

Algumas descrições de especificadores de formato numérico padrão referem-se a tipos inteiros ou de ponto flutuante. Os tipos numéricos integrais são [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) e [BigInteger](xref:System.Numerics.BigInteger). Os tipos numéricos de ponto flutuante são [Decimal](xref:System.Decimal), [Single](xref:System.Single) e [Double](xref:System.Double). 

### <a name="floating-point-infinities-and-nan"></a>Infinitos de ponto flutuante e NaN

Independentemente da cadeia de caracteres de formato, se o valor de um tipo de ponto flutuante [Single](xref:System.Single) ou [Double](xref:System.Double) é infinito positivo, infinito negativo ou não é um número (NaN), a cadeia de caracteres formatada é o valor das respectivas propriedades [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol), [NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) ou [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) especificadas pelo objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) aplicável no momento.

## <a name="example"></a>Exemplo

O exemplo a seguir formata um inteiro e um valor numérico de ponto flutuante usando a cultura en-US e todos os especificadores de formato numérico padrão. Este exemplo usa dois tipos numéricos específicos ([Double](xref:System.Double) e [Int32](xref:System.Int32)), mas poderia produzir resultados semelhantes para qualquer um dos outros tipos base numéricos ([Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [Int64](xref:System.Int64), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) e [BigInteger](xref:System.Numerics.BigInteger), [Decimal](xref:System.Decimal) e [Single](xref:System.Single)). 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class NumericFormats
{
   public static void Main()
   {
      // Display string representations of numbers for en-us culture
      CultureInfo ci = new CultureInfo("en-us");

      // Output floating point values
      double floating = 10761.937554;
      Console.WriteLine("C: {0}", 
              floating.ToString("C", ci));           // Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", 
              floating.ToString("E03", ci));         // Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", 
              floating.ToString("F04", ci));         // Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}",  
              floating.ToString("G", ci));           // Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", 
              floating.ToString("N03", ci));         // Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", 
              (floating/10000).ToString("P02", ci)); // Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", 
              floating.ToString("R", ci));           // Displays "R: 10761.937554"            
      Console.WriteLine();

      // Output integral values
      int integral = 8395;
      Console.WriteLine("C: {0}", 
              integral.ToString("C", ci));           // Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", 
              integral.ToString("D6", ci));          // Displays "D: 008395" 
      Console.WriteLine("E: {0}", 
              integral.ToString("E03", ci));         // Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", 
              integral.ToString("F01", ci));         // Displays "F: 8395.0"    
      Console.WriteLine("G: {0}",  
              integral.ToString("G", ci));           // Displays "G: 8395"
      Console.WriteLine("N: {0}", 
              integral.ToString("N01", ci));         // Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", 
              (integral/10000.0).ToString("P02", ci)); // Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", 
              integral.ToString("X", ci));           // Displays "X: 0x20CB"
      Console.WriteLine();
   }
}
```

```vb
Option Strict On

Imports System.Globalization
Imports System.Threading

Module NumericFormats
   Public Sub Main()
      ' Display string representations of numbers for en-us culture
      Dim ci As New CultureInfo("en-us")

      ' Output floating point values
      Dim floating As Double = 10761.937554
      Console.WriteLine("C: {0}", _
              floating.ToString("C", ci))           ' Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", _
              floating.ToString("E03", ci))         ' Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", _
              floating.ToString("F04", ci))         ' Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}", _ 
              floating.ToString("G", ci))           ' Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", _
              floating.ToString("N03", ci))         ' Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", _
              (floating/10000).ToString("P02", ci)) ' Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", _
              floating.ToString("R", ci))           ' Displays "R: 10761.937554"            
      Console.WriteLine()

      ' Output integral values
      Dim integral As Integer = 8395
      Console.WriteLine("C: {0}", _
              integral.ToString("C", ci))           ' Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", _
              integral.ToString("D6"))              ' Displays "D: 008395" 
      Console.WriteLine("E: {0}", _
              integral.ToString("E03", ci))         ' Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", _
              integral.ToString("F01", ci))         ' Displays "F: 8395.0"    
      Console.WriteLine("G: {0}", _ 
              integral.ToString("G", ci))           ' Displays "G: 8395"
      Console.WriteLine("N: {0}", _
              integral.ToString("N01", ci))         ' Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", _
              (integral/10000).ToString("P02", ci)) ' Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", _
              integral.ToString("X", ci))           ' Displays "X: 0x20CB"
      Console.WriteLine()
   End Sub
End Module
```

## <a name="see-also"></a>Consulte também

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[Cadeias de caracteres de formato numérico personalizado](custom-numeric.md)

[Formatando tipos](formatting-types.md)

[Como preencher um número com zeros à esquerda](pad-number.md)

[Formatação de composição](composite-format.md)



<!--HONumber=Nov16_HO3-->


