---
title: -deterministic (Opções do Compilador C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6dd597f726b5bbc40feb4cc6f5b03acabd92f4a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a>-deterministic

Faz com que o compilador produza um assembly cuja saída byte a byte é idêntica entre compilações para entradas idênticas. 

## <a name="syntax"></a>Sintaxe

```
-deterministic
```

## <a name="remarks"></a>Comentários

Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, uma vez que o compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios. Use a opção `-deterministic` para produzir um *assembly determinística*, cujo conteúdo binário seja idêntico entre compilações, desde que a entrada permaneça a mesma.

O compilador considera as seguintes entradas com a finalidade de determinismo:

- A sequência de parâmetros de linha de comando.
- O conteúdo do arquivo de resposta .rsp do compilador.
- A versão precisa do compilador usado e seus assemblies referenciados.
- O caminho do diretório atual.
- O conteúdo binário de todos os arquivos passados explicitamente para o compilador direta ou indiretamente, incluindo:
    - Arquivos de origem
    - Assemblies referenciados
    - Módulos referenciados
    - Recursos
    - O arquivo de chave de nome forte
    - @ arquivos de resposta
    - Analisadores
    - Conjuntos de regras
    - Arquivos adicionais que podem ser usados por analisadores
- A cultura atual (para o idioma no qual as mensagens de diagnóstico e exceção são produzidas).
- A codificação padrão (ou a página de código atual) se a codificação não for especificada.
- A existência, a inexistência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificados, por exemplo, por `/lib` ou `/recurse`).
- A plataforma CLR na qual o compilador é executado.
- O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.

Quando as fontes estão disponíveis publicamente, a compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável. Isso também pode ser útil em um sistema de compilação contínua para determinar se as etapas de compilação dependentes de alterações para um binário precisam ser executadas. 

## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
