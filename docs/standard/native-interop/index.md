---
title: Interoperabilidade Nativa – .NET
description: Saiba como fazer interface com componentes nativos no .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b01ea9c17db6da32755309d9c1c2359cecaa1155
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062716"
---
# <a name="native-interoperability"></a>Interoperabilidade nativa

Os artigos a seguir mostram várias maneiras de fazer "interoperabilidade nativa" no .NET.

Existem alguns motivos para chamar em código nativo:

* Os sistemas operacionais vêm com um grande volume de APIs que não estão presentes nas bibliotecas de classes gerenciadas. Um exemplo perfeito para esse cenário seria o acesso a funções de gerenciamento de hardware ou do sistema operacional.
* Comunicação com outros componentes que têm ou podem produzir ABIs de estilo C (ABIs nativas), como o código Java que é exposto via [JNI (Interface Nativa do Java)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) ou qualquer outra linguagem gerenciada que pode produzir um componente nativo.
* No Windows, a maioria dos softwares que são instalados, como o pacote Microsoft Office, registra os componentes COM que representam seus programas e permitem que sejam automatizados ou usados pelos desenvolvedores. Isso também requer interoperabilidade nativa.

A lista acima não abrange todas as possíveis situações e cenários em que o desenvolvedor desejaria/gostaria de/precisaria fazer interface com componentes nativos. A biblioteca de classes do .NET, por exemplo, usa o suporte para interoperabilidade nativa para implementar um número razoável de APIs, como suporte ao console e manipulação, acesso ao sistema de arquivos e outras. No entanto, é importante observar que há uma opção, se necessário.

> [!NOTE]
> A maioria dos exemplos nesta seção será apresentada para todas as três plataformas com suporte para .NET Core (Windows, Linux e macOS). No entanto, para alguns exemplos ilustrativos e curtos, é exibida apenas uma amostra que usa nomes de arquivo e extensões do Windows (ou seja, "dll" para bibliotecas). Isso não significa que tais recursos não estão disponíveis em Linux ou macOS; foi feito simplesmente para maior conveniência.

## <a name="see-also"></a>Consulte também

- [Invocação de plataforma (P/Invoke)](pinvoke.md)
- [Marshaling de tipo](type-marshaling.md)
- [Melhores práticas de interoperabilidade nativa](best-practices.md)
