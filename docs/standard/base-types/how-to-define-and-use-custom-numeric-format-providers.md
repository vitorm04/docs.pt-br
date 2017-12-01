---
title: "Como definir e usar provedores de formatos numéricos personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- custom numeric format strings
- numbers [.NET Framework], custom numeric format strings
- displaying date and time data
- format providers [.NET Framework]
- custom format strings
ms.assetid: a281bfbf-6596-45ed-a2d6-3782d535ada2
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e44a909eb92f0d9dfa21980a918a2d370dcf427
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Como definir e usar provedores de formatos numéricos personalizados
O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] lhe dá controle abrangente sobre a representação de cadeia de caracteres de valores numéricos. Ele dá suporte aos seguintes recursos para personalizar o formato de valores numéricos:  
  
-   Cadeias de caracteres de formato numérico padrão, que fornecem um conjunto predefinido de formatos para converter números para suas representações de cadeia de caracteres. Você pode usá-las com qualquer método de formatação, como numérica <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, que tem um `format` parâmetro. Para obter detalhes, consulte [cadeias de caracteres de formato numérico padrão](../../../docs/standard/base-types/standard-numeric-format-strings.md).  
  
-   Cadeias de caracteres de formato numérico personalizado, que fornecem um conjunto de símbolos que podem ser combinados para definir especificadores de formato numérico personalizado. Eles também podem ser usados com qualquer método de formatação, como numérica <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType>, que tem um `format` parâmetro. Para obter detalhes, consulte [cadeias de caracteres de formato numérico personalizado](../../../docs/standard/base-types/custom-numeric-format-strings.md).  
  
-   Personalizar <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> objetos, que definem os símbolos e padrões de formato usados para exibir as representações de cadeia de caracteres de valores numéricos. Você pode usá-las com qualquer método de formatação, como numérica <xref:System.Int32.ToString%2A>, que tem um `provider` parâmetro. Normalmente, o `provider` parâmetro é usado para especificar formatação de cultura específica.  
  
 Em alguns casos (como quando um aplicativo deve exibir um número de conta formatado, um número de identificação ou um código postal) essas três técnicas são inadequadas. O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] também permite que você defina um objeto de formatação que não é nem um <xref:System.Globalization.CultureInfo> nem um <xref:System.Globalization.NumberFormatInfo> objeto para determinar como um valor numérico é formatado. Este tópico fornece informações passo a passo para implementar esse tipo de objeto, bem como um exemplo que formata números de telefone.  
  
### <a name="to-define-a-custom-format-provider"></a>Para definir um provedor de formato personalizado  
  
1.  Definir uma classe que implementa o <xref:System.IFormatProvider> e <xref:System.ICustomFormatter> interfaces.  
  
2.  Implementar o método de <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> . <xref:System.IFormatProvider.GetFormat%2A>é um método de retorno de chamada que o método de formatação (como o <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> método) invoca para recuperar o objeto que é realmente responsável por executar a formatação personalizada. Uma implementação típica de <xref:System.IFormatProvider.GetFormat%2A> faz o seguinte:  
  
    1.  Determina se o <xref:System.Type> objeto passado como um método de parâmetro representa um <xref:System.ICustomFormatter> interface.  
  
    2.  Se o parâmetro representar a <xref:System.ICustomFormatter> interface, <xref:System.IFormatProvider.GetFormat%2A> retorna um objeto que implementa o <xref:System.ICustomFormatter> interface que é responsável por fornecer formatação personalizada. Normalmente, o objeto de formatação personalizado retorna a si próprio.  
  
    3.  Se o parâmetro não representam o <xref:System.ICustomFormatter> interface, <xref:System.IFormatProvider.GetFormat%2A> retorna `null`.  
  
3.  Implementar o método de <xref:System.ICustomFormatter.Format%2A> . Este método é chamado pelo <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> método e é responsável por retornar a representação de cadeia de caracteres de um número. Implementar o método normalmente envolve o seguinte:  
  
    1.  Opcionalmente, certifique-se de que o método é legitimamente destinado a fornecer serviços de formatação examinando o `provider` parâmetro. Para formatar objetos que implementam ambos <xref:System.IFormatProvider> e <xref:System.ICustomFormatter>, isso envolve testar o `provider` parâmetro para igualdade com o objeto atual de formatação.  
  
    2.  Determine se o objeto de formatação deve dar suporte a especificadores de formato personalizado. (Por exemplo, um especificador de formato "N" pode indicar que um número de telefone dos EUA deve ser gerado no formato NANP e um "I" pode indicar a saída no formato E. 123 da Recomendação ITU-T.) Se especificadores de formato forem usados, o método deve tratar o especificador de formato específico. Ele é passado para o método de `format` parâmetro. Se nenhum especificador estiver presente, o valor da `format` parâmetro é <xref:System.String.Empty?displayProperty=nameWithType>.  
  
    3.  Recuperar o valor numérico é passado para o método como o `arg` parâmetro. Execute as manipulações que forem necessárias para convertê-lo em sua representação de cadeia de caracteres.  
  
    4.  Retornar a representação de cadeia de caracteres da `arg` parâmetro.  
  
### <a name="to-use-a-custom-numeric-formatting-object"></a>Para usar um objeto de formatação numérico personalizado  
  
1.  Crie uma nova instância da classe de formatação personalizada.  
  
2.  Chamar o <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> método de formatação, passando o objeto de formatação personalizado, o especificador de formatação (ou <xref:System.String.Empty?displayProperty=nameWithType>, se não for usado) e o valor numérico a ser formatado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um provedor de formato numérico personalizado chamado `TelephoneFormatter`, que converte um número que representa um número de telefone dos EUA para seu formato NANP ou E.123. O método lida com dois especificadores de formato, "N" (que gera o formato NANP) e "I" (que gera o formato internacional E.123).  
  
 [!code-csharp[Formatting.HowTo.NumericValue#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#1)]
 [!code-vb[Formatting.HowTo.NumericValue#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#1)]  
  
 O provedor de formato numérico personalizado pode ser usado apenas com o <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> método. As outras sobrecargas de métodos de formatação numérica (como `ToString`) que têm um parâmetro de tipo <xref:System.IFormatProvider> passam por todos os a <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> implementação um <xref:System.Type> objeto que representa o <xref:System.Globalization.NumberFormatInfo> tipo. No retorno, eles esperam que o método para retornar um <xref:System.Globalization.NumberFormatInfo> objeto. Se não estiver, o provedor de formato numérico personalizado será ignorado e o <xref:System.Globalization.NumberFormatInfo> do objeto para a cultura atual é usada em seu lugar. No exemplo, o `TelephoneFormatter.GetFormat` método trata a possibilidade de que ele pode ser inadequadamente passado para uma método de formatação examinando o parâmetro do método e retornando numérica `null` se ele representa um tipo diferente de <xref:System.ICustomFormatter>.  
  
 Se um provedor de formato numérico personalizado oferece suporte a um conjunto de especificadores de formato, certifique-se de fornecer um comportamento padrão se nenhum especificador de formato é fornecido no item de formato usado no <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> chamada de método. No exemplo, "N" é o especificador de formato padrão. Isso permite que um número a ser convertido em um número de telefone formatado, fornecendo um especificador de formato explícito. O exemplo a seguir ilustra essa chamada de método.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#2)]
 [!code-vb[Formatting.HowTo.NumericValue#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#2)]  
  
 Mas também permite que a conversão ocorra se nenhum especificador de formato estiver presente. O exemplo a seguir ilustra essa chamada de método.  
  
 [!code-csharp[Formatting.HowTo.NumericValue#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.NumericValue/cs/Telephone1.cs#3)]
 [!code-vb[Formatting.HowTo.NumericValue#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.NumericValue/vb/Telephone1.vb#3)]  
  
 Se nenhum especificador de formato padrão for definido, sua implementação do <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> método deve incluir código como o seguinte para que o .NET pode fornecer a formatação que seu código não oferece suporte.  
  
 [!code-csharp[System.ICustomFormatter.Format#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.ICustomFormatter.Format/cs/format.cs#1)]
 [!code-vb[System.ICustomFormatter.Format#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.ICustomFormatter.Format/vb/Format.vb#1)]  
  
 No caso de neste exemplo, o método que implementa <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> é destinado a servir como um método de retorno de chamada para o <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> método. Portanto, ele examina o `formatProvider` parâmetro para determinar se ele contém uma referência ao atual `TelephoneFormatter` objeto. No entanto, o método também pode ser chamado diretamente do código. Nesse caso, você pode usar o `formatProvider` parâmetro para fornecer uma <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> objeto que fornece informações de formatação específica da cultura.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Compile o código na linha de comando com csc.exe ou vb.exe. Para compilar o código em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], coloque-o em um modelo de projeto de aplicativo de console.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)
