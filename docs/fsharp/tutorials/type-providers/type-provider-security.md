---
title: Segurança do provedor de tipos
description: Saiba mais sobre a segurança do provedor de tipo no F#, inclusive sobre como alterar as configurações de confiança para um provedor de tipo.
ms.date: 05/16/2016
ms.openlocfilehash: 9ccb33d7298736c3d6b54980b6fe09bc9f2e0259
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611185"
---
# <a name="type-provider-security"></a>Segurança do provedor de tipos

Provedores de tipos são assemblies (DLLs) referenciados pelo seu F# projeto ou script que contêm código para se conectar a fontes de dados externas e superfície essas informações de tipo para o F# digite ambiente. Normalmente, o código em assemblies referenciados é executado somente quando você compila e, em seguida, execute o código (ou no caso de um script, enviar o código para F# interativo). No entanto, um assembly do provedor de tipo será executado dentro do Visual Studio quando o código for simplesmente navegar no editor. Isso acontece porque os provedores de tipos precisam executar para adicionar informações extras para o editor, como dicas de ferramenta informações rápidas, conclusões de IntelliSense e assim por diante. Como resultado, há considerações de segurança extra para o tipo de assemblies do provedor, como eles são executados automaticamente dentro do processo do Visual Studio.

## <a name="security-warning-dialog"></a>Caixa de diálogo de aviso de segurança

Ao usar um assembly do provedor de tipo específico pela primeira vez, o Visual Studio exibe uma caixa de diálogo de segurança que avisa que o provedor de tipos está prestes a executar. Antes do Visual Studio carrega o provedor de tipo, ele dá a oportunidade de decidir se você confiar neste provedor específico. Se você confiar na origem do provedor de tipo, em seguida, selecione "Posso confiar neste provedor de tipo." Se você não confiar na origem do provedor de tipo, em seguida, selecione "Eu não confiar neste provedor de tipo". Confiantes o provedor permite que ele seja executado dentro do Visual Studio e fornecer o IntelliSense e criar recursos. Mas, se o provedor de tipos é mal-intencionado, executar seu código pode comprometer a sua máquina.

Se seu projeto contém código que faz referência a provedores de tipos que você escolheu na caixa de diálogo para não confiar, em seguida, em tempo de compilação, o compilador reportará um erro que indica que o provedor de tipo não é confiável. Quaisquer tipos que são dependentes no provedor de tipo não confiáveis são indicados por linhas onduladas vermelhas. É seguro procurar o código no editor.

Se você decidir alterar a configuração de confiança diretamente no Visual Studio, execute as seguintes etapas.

### <a name="to-change-the-trust-settings-for-type-providers"></a>Para alterar as configurações de confiança para provedores de tipos

1. Sobre o `Tools` menu, selecione `Options`e expanda o `F# Tools` nó.

2. Selecione `Type Providers`, na lista de provedores de tipos, marque a caixa de seleção de provedores de tipos que você confia e desmarque a caixa de seleção para aqueles que você não confia.

## <a name="see-also"></a>Consulte também

- [Provedores de Tipos](index.md)