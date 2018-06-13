---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb1d27f614afc3b07f9d663831fc2071535236f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653202"
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
[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
[Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
