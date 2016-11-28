---
title: "Numéricos no .NET Core"
description: "Numéricos no .NET Core"
keywords: .NET, .NET Core
author: rpetrusha
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6b8696be-55f5-4b66-98f3-69ff827c2c49
translationtype: Human Translation
ms.sourcegitcommit: d5c7a18af16b4f3416e84b6cf86f0f78f28948da
ms.openlocfilehash: 2930bf6879df3cd16cbd0221ae6dfcba9b41de2e

---

# <a name="numerics-in-net-core"></a>Numéricos no .NET Core

O .NET Core dá suporte aos integrais numéricos padrão e aos primitivos de ponto flutuante, bem como [System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger), um tipo integral sem limite teórico superior ou inferior [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex), um tipo que representa números complexos e um conjunto de tipos de vetores habilitados por [SIMD](https://en.wikipedia.org/wiki/SIMD) (Single Instruction Multiple Data) no namespace [System.Numerics](https://docs.microsoft.com/dotnet/core/api/System.Numerics). 

## <a name="integral-types"></a>Tipos integrais

O .NET Core dá suporte a inteiros assinados e não assinados que variam de um byte a oito bytes de comprimento. A tabela a seguir lista os tipos integrais e seu tamanho, indica se são assinados ou não assinados e documenta seu intervalo. Todos os inteiros são tipos de valor. 

Tipo | Assinado/não assinado | Tamanho (bytes) | Valor Mínimo | Valor Máximo
---- | --------------- | ------------ | ------------- | -------------
[System.Byte](https://docs.microsoft.com/dotnet/core/api/System.Byte) | Não assinado | 1 | 0 | 255
[System.Int16](https://docs.microsoft.com/dotnet/core/api/System.Int16) | Assinado | 2 | -32,768 | 32,767
[System.Int32](https://docs.microsoft.com/dotnet/core/api/System.Int32) | Assinado | 4 | -2,147,483,648 | 2,147,483,647
[System.Int64](https://docs.microsoft.com/dotnet/core/api/System.Int64) | Assinado | 8 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807
[System.SByte](https://docs.microsoft.com/dotnet/core/api/System.SByte) | Assinado | 1 | -128 | 127
[System.UInt16](https://docs.microsoft.com/dotnet/core/api/System.UInt16) | Não assinado | 2 | 0 | 65,535
[System.UInt32](https://docs.microsoft.com/dotnet/core/api/System.UInt32) | Não assinado | 4 | 0 | 4,294,967,295
[System.UInt64](https://docs.microsoft.com/dotnet/core/api/System.UInt64) | Não assinado | 8 | 0 | 18,446,744,073,709,551,615

Cada tipo de integral dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita. Cada inteiro também inclui métodos para executar comparações de igualdade e comparações relativas, para converter a representação de cadeia de caracteres de um número para esse inteiro e para converter um inteiro na sua representação de cadeia de caracteres. Algumas operações matemáticas adicionais além das manipuladas pelos operadores padrão, como arredondamento e identificação do valor maior ou menor de dois inteiros, estão disponíveis na classe [System.Math](https://docs.microsoft.com/dotnet/core/api/System.Math). Você também pode trabalhar com os bits individuais em um valor inteiro usando a classe [System.BitConverter](https://docs.microsoft.com/dotnet/core/api/System.BitConverter). 
     
Observe que os tipos integrais não assinados não são compatíveis com CLS. Para obter mais informações, consulte [Common Type System e Common Language Specification do .NET](common-type-system.md).

## <a name="floating-point-types"></a>Tipos de ponto flutuante

O .NET Core inclui três primitivos tipos de ponto flutuante, que estão listados na tabela a seguir. 

Tipo | Tamanho (bytes) | Valor Mínimo | Valor Máximo
---- | ------------ | ------------- | -------------
[System.Double](https://docs.microsoft.com/dotnet/core/api/System.Double) | 8 | -1.79769313486232e308 | 1.79769313486232e308
[System.Single](https://docs.microsoft.com/dotnet/core/api/System.Single) | 4 | -3.402823e38 | 3.402823e38
[System.Decimal](https://docs.microsoft.com/dotnet/core/api/System.Decimal) | 16 | -79,228,162,514,264,337,593,543,950,335 | 79,228,162,514,264,337,593,543,950,335
   
Cada tipo de ponto flutuante dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita. Cada um também inclui métodos para executar comparações de igualdade e comparações relativas, para converter a representação de cadeia de caracteres de um número de ponto flutuante e para converter um número de ponto flutuante em sua representação de cadeia de caracteres. Algumas operações matemáticas, algébricas e trigonométricas adicionais são disponibilizadas pela classe `Math`. Você também pode trabalhar com os bits individuais nos valores `Double` e `Single` usando a classe `BitConverter`. A estrutura `Decimal` tem seus próprios métodos `Decimal.GetBits` e `Decimal.Decimal(Int32())`, para trabalhar com os bits individuais de um valor decimal, assim como seu próprio conjunto de métodos para executar algumas operações matemáticas adicionais. 

Os tipos `Double` e `Single` destinam-se a ser usados para valores que, por sua natureza, são imprecisos (como a distância entre duas estrelas do sistema solar) e para aplicativos em que um alto grau de precisão e erro de arredondamento pequeno não são necessários. Você deve usar o tipo `Decimal` para casos em que uma maior precisão é necessária e erro de arredondamento é indesejável.

## <a name="biginteger"></a>BigInteger

[System.Numerics.BigInteger](https://docs.microsoft.com/dotnet/core/api/System.Numerics.BigInteger) é um tipo imutável que representa um inteiro arbitrariamente grande cujo valor, em teoria, não tem limites superiores ou inferiores. Os métodos do tipo `BigInteger` são muito semelhantes aos dos outros tipos integrais.  

## <a name="complex"></a>Complexo

O tipo [System.Numerics.Complex](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Complex) representa um número complexo, ou seja, um número com uma parte de número real e uma parte de número imaginário. Dá suporte a um conjunto padrão de aritmética, de comparação, de igualdade, de conversão explícita e operadores de conversão implícita, bem como a métodos matemáticos, algébricos e trigonométricos. 

## <a name="simd-enabled-vector-types"></a>Tipos de vetor habilitados para SIMD

O namespace `System.Numerics` inclui um conjunto de tipos de vetor habilitados para SIMD para o .NET Core. O SIMD permite que algumas operações se tornem paralelas no nível de hardware, o que resulta em enormes melhorias de desempenho em aplicativos matemáticos, científicos e gráficos que executam cálculos em vetores. 

Os tipos de vetor habilitados para SMID no .NET Core incluem o seguinte: 

* Tipos [System.Numerics.Vector2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector2), [System.Numerics.Vector3](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector3) e [System.Numerics.Vector4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector4), que são vetores do tipo em duas, três e quatro dimensões	`Single`.

* A estrutura [Vector&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Vector-1) que permite criar um vetor de qualquer tipo numérico primitivo. Os tipos numéricos primitivos incluem todos os tipos numéricos no namespace System, exceto Decimal.

* Dois tipos de matriz, [System.Numerics.Matrix3x2](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix3x2), que representa uma matriz 3x2; e [System.Numerics.Matrix4x4](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Matrix4x4), que representa uma matriz 4x4. 

* O tipo [System.Numerics.Plane](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Plane), que representa um plano tridimensional e o tipo [System.Numerics.Quaternion](https://docs.microsoft.com/dotnet/core/api/System.Numerics.Quaternion), que representa um vetor usado para codificar rotações físicas tridimensionais.



<!--HONumber=Nov16_HO4-->


