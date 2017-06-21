---
title: "#<a name=\"pragma-checksum-c-reference--microsoft-docs\"></a>soma de verificação pragma (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: acb554a757886d1924fa7ef69814b98b3b440871
ms.contentlocale: pt-br
ms.lasthandoff: 06/15/2017

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
 O GUID (identificador global exclusivo) do arquivo.  
  
 `"checksum_bytes"`  
 A cadeia de caracteres de dígitos hexadecimais que representa os bytes da soma de verificação. Deve ser um número par de dígitos hexadecimais. Um número ímpar de dígitos resulta em um aviso em tempo de compilação e a diretiva é ignorada.  
  
## <a name="remarks"></a>Comentários  
 O depurador do Visual Studio usa uma soma de verificação para certificar-se de sempre encontrar a fonte correta. O compilador calcula a soma de verificação para um arquivo de origem e, em seguida, emite a saída no arquivo PDB (banco de dados do programa). Em seguida, o depurador usa o PDB para comparar com a soma de verificação que ele calcula para o arquivo de origem.  
  
 Essa solução não funciona para projetos [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], porque é a soma de verificação calculada é para o arquivo de origem gerado e não para o arquivo .aspx. Para resolver esse problema, a `#pragma checksum` fornece suporte à soma de verificação para páginas do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Quando você cria um projeto do [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] no [!INCLUDE[csprcs](~/includes/csprcs-md.md)], o arquivo de origem gerado contém uma soma de verificação para o arquivo .aspx, do qual a fonte é gerada. Então, o compilador grava essas informações no arquivo PDB.  
  
 Se o compilador não encontrar uma diretiva `#pragma checksum` no arquivo, ele calcula a soma de verificação e grava o valor no arquivo PDB.  
  
## <a name="example"></a>Exemplo  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)

