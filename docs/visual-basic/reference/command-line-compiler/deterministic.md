---
title: -determinística
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a>-determinística

Faz com que o compilador produzir um assembly cuja saída de byte a byte é idêntica em compilações para entradas idênticas. 

## <a name="syntax"></a>Sintaxe

```
-deterministic
```

## <a name="remarks"></a>Comentários

Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, desde que o compilador adiciona um carimbo de hora e um GUID que é gerado a partir de números aleatórios. Usar o `-deterministic` opção para produzir um *assembly determinística*, cujo conteúdo binário é idêntico em compilações desde que a entrada permanece o mesmo.

O compilador considera as seguintes entradas com a finalidade de determinismo:

- A sequência de parâmetros de linha de comando.
- O conteúdo do arquivo de resposta do compilador. rsp.
- A versão precisa do compilador usado e seus assemblies referenciados.
- O caminho do diretório atual.
- O conteúdo binário de todos os arquivos passado explicitamente para o compilador direta ou indiretamente, incluindo: 
    - Arquivos de origem
    - assemblies referenciados
    - Módulos referenciados
    - Recursos
    - O arquivo de chave de nome forte
    - @ arquivos de resposta
    - Analisadores
    - Conjuntos de regras
    - Arquivos adicionais que podem ser usados por analisadores
- A cultura atual (para o idioma no qual diagnóstico e a exceção são produzidas mensagens).
- A codificação padrão (ou a página de código atual) se a codificação não for especificada.
- A existência, a não-existência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificado, por exemplo, `/lib` ou `/recurse`).
- A plataforma CLR no qual o compilador é executado.
- O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.

Quando fontes disponíveis publicamente, compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável. Ele também pode ser útil em um sistema de compilação contínua para determinar se precisam de etapas de compilação que são dependentes de alterações em um binário a ser executado. 

## <a name="see-also"></a>Consulte também
[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
[Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
