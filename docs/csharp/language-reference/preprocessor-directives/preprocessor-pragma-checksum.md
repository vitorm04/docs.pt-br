---
title: '#soma de verificação pragma (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 28a9ccfb9d36e648304a177294904ab1b7f18892
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45614496"
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (Referência de C#)
Gera somas de verificação para os arquivos de origem para ajudar na depuração de páginas do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `"filename"`  
 O nome do arquivo que exige o monitoramento de alterações ou atualizações.  
  
 `"{guid}"`  
 O GUID (identificador global exclusivo) do algoritmo de hash.  
  
 `"checksum_bytes"`  
 A cadeia de caracteres de dígitos hexadecimais que representa os bytes da soma de verificação. Deve ser um número par de dígitos hexadecimais. Um número ímpar de dígitos resulta em um aviso em tempo de compilação e a diretiva é ignorada.  
  
## <a name="remarks"></a>Comentários  
 O depurador do Visual Studio usa uma soma de verificação para certificar-se de sempre encontrar a fonte correta. O compilador calcula a soma de verificação para um arquivo de origem e, em seguida, emite a saída no arquivo PDB (banco de dados do programa). Em seguida, o depurador usa o PDB para comparar com a soma de verificação que ele calcula para o arquivo de origem.  
  
 Essa solução não funciona para projetos [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], porque é a soma de verificação calculada é para o arquivo de origem gerado e não para o arquivo .aspx. Para resolver esse problema, a `#pragma checksum` fornece suporte à soma de verificação para páginas do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Quando você cria um projeto do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] em Visual C#, o arquivo de origem gerado contém uma soma de verificação para o arquivo .aspx, do qual a fonte é gerada. Então, o compilador grava essas informações no arquivo PDB.  
  
 Se o compilador não encontrar uma diretiva `#pragma checksum` no arquivo, ele calcula a soma de verificação e grava o valor no arquivo PDB.  
  
## <a name="example"></a>Exemplo  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)
