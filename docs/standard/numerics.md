---
title: "Numéricos no  .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 087c1cc56abf2a00544e22023ce72fae670df369
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="numerics-in-the-net-framework"></a>Numéricos no  .NET Framework
O .NET Core dá suporte aos integrais numéricos padrão e aos primitivos de ponto flutuante, bem como <xref:System.Numerics.BigInteger>, um tipo integral sem limite teórico superior ou inferior <xref:System.Numerics.Complex>, um tipo que representa números complexos e um conjunto de tipos de vetores habilitados por SIMD no namespace <xref:System.Numerics>.  
  
 Além disso, System.Numerics.Vectors, a biblioteca de tipos de vetor habilitados para SIMD foi lançada como um pacote do NuGet.  
  
## <a name="integral-types"></a>Tipos integrais  
 O .NET Framework dá suporte a inteiros assinados e não assinados que variam de um byte a oito bytes de comprimento. A tabela a seguir lista os tipos integrais e seu tamanho, indica se são assinados ou não assinados e documenta seu intervalo. Todos os inteiros são tipos de valor.  
  
|Tipo|Assinado/não assinado|Tamanho (bytes)|Valor mínimo|Valor Máximo|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=fullName>|Não assinado|1|0|255|  
|<xref:System.Int16?displayProperty=fullName>|Assinado|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=fullName>|Assinado|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=fullName>|Assinado|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=fullName>|Assinado|1|-128|127|  
|<xref:System.UInt16?displayProperty=fullName>|Não assinado|2|0|65,535|  
|<xref:System.UInt32?displayProperty=fullName>|Não assinado|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=fullName>|Não assinado|8|0|18,446,744,073,709,551,615|  
  
 Cada tipo de integral dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita. Cada inteiro também inclui métodos para executar comparações de igualdade e comparações relativas, para converter a representação de cadeia de caracteres de um número para esse inteiro e para converter um inteiro na sua representação de cadeia de caracteres. Algumas operações matemáticas adicionais além das manipuladas pelos operadores padrão, como arredondamento e identificação do valor maior ou menor de dois inteiros, estão disponíveis na classe <xref:System.Math>. Você também pode trabalhar com os bits individuais nos valores usando a classe <xref:System.BitConverter>.  
  
 Observe que os tipos integrais não assinados não são compatíveis com CLS. Para saber mais, veja [Componentes de independência de linguagem e componentes independentes da linguagem](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Tipos de ponto flutuante  
 O .NET Framework inclui três primitivos tipos de ponto flutuante, que estão listados na tabela a seguir.  
  
|Tipo|Tamanho (em bytes)|Mínimo|Máximo|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=fullName>|8|-1.79769313486232e308|1.79769313486232e308|  
|<xref:System.Single?displayProperty=fullName>|4|-3.402823e38|3.402823e38|  
|<xref:System.Decimal?displayProperty=fullName>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Cada tipo de ponto flutuante dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita. Cada um também inclui métodos para executar comparações de igualdade e comparações relativas, para converter a representação de cadeia de caracteres de um número de ponto flutuante e para converter um número de ponto flutuante em sua representação de cadeia de caracteres. Algumas operações matemáticas, algébricas e trigonométricas adicionais são disponibilizadas pela classe <xref:System.Math>. Você também pode trabalhar com os bits individuais nos valores <xref:System.Double> e <xref:System.Single> usando a classe <xref:System.BitConverter>. A estrutura <xref:System.Decimal?displayProperty=fullName> tem seus próprios métodos <xref:System.Decimal.GetBits%2A?displayProperty=fullName> e <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=fullName>, para trabalhar com os bits individuais de um valor decimal, assim como seu próprio conjunto de métodos para executar algumas operações matemáticas adicionais.  
  
 Os tipos <xref:System.Double> e <xref:System.Single> destinam-se a ser usados para valores que, por sua natureza, são imprecisos (como a distância entre duas estrelas do sistema solar) e para aplicativos em que um alto grau de precisão e erro de arredondamento pequeno não são necessários. Você deve usar o tipo <xref:System.Decimal?displayProperty=fullName> para casos em que uma maior precisão é necessária e o erro de arredondamento é indesejável,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=fullName> é um tipo imutável que representa um inteiro arbitrariamente grande cujo valor, em teoria, não tem limites superiores ou inferiores. Os métodos do tipo <xref:System.Numerics.BigInteger> são muito semelhantes aos dos outros tipos integrais.  
  
## <a name="complex"></a>Complexo  
 O tipo <xref:System.Numerics.Complex> representa um número complexo, ou seja, um número com uma parte de número real e uma parte de número imaginário. Dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita, bem como a métodos matemáticos, algébricos e trigonométricos.  
  
## <a name="simd-enabled-vector-types"></a>Tipos de vetor habilitados para SIMD  
 O namespace <xref:System.Numerics> inclui um conjunto de tipos de vetor habilitados para SIMD para o .NET Framework. O SIMD (operações Single Instruction Multiple Data) permite que algumas operações se tornem paralelas no nível de hardware, o que resulta em enormes melhorias de desempenho em aplicativos matemáticos, científicos e gráficos que executam cálculos em vetores.  
  
 Os tipos de vetor habilitados para SMID no .NET Framework incluem o seguinte:  Além disso, System.Numerics.Vectors inclui um Tipo de plano e um tipo Quaternion.  
  
-   Os tipos <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> e <xref:System.Numerics.Vector4>, que são vetores de 2, 3 e 4 dimensões do tipo <xref:System.Single>.  
  
-   Dois tipos de matriz, <xref:System.Numerics.Matrix3x2>, que representa uma matriz 3x2, e <xref:System.Numerics.Matrix4x4>, que representa uma matriz de 4x4.  
  
-   Os tipos <xref:System.Numerics.Plane> e <xref:System.Numerics.Quaternion>.  
  
 Os tipos de vetor habilitados para SimD são implementados em IL, o que permite que sejam utilizados em hardware não habilitados para SimD e compiladores JIT. Para tirar proveito das instruções SIMD, seus aplicativos de 64 bits devem ser compilados pelo novo compilador JIT de 64 bits para código gerenciado, que é incluído com o .NET Framework 4.6; ele adiciona suporte a SIMD ao direcionar para processadores x64.  
  
 O SIMD também pode ser baixado como um [pacote do NuGet](http://www.nuget.org/packages/System.Numerics.Vectors).  O pacote NutGET também inclui uma estrutura <xref:System.Numerics.Vector%601> genérica que permite a criação de um vetor de qualquer tipo numérico primitivo. (Os tipos numéricos primitivos incluem todos os tipos numéricos no namespace <xref:System>, exceto para <xref:System.Decimal>.) Além disso, a estrutura <xref:System.Numerics.Vector%601> fornece uma biblioteca de métodos de conveniência que você pode chamar ao trabalhar com vetores.  
  
## <a name="see-also"></a>Consulte também  
 [Fundamentos do aplicativo](../../docs/standard/application-essentials.md)

