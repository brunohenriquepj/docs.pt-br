---
title: Noções básicas de criação de contêiner comum
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: c67986b1deb504f2b05f2903a263bf1a91f70b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568115"
---
# <a name="common-container-design-principles"></a>Noções básicas de criação de contêiner comum

Em frente de obter no processo de desenvolvimento, há alguns conceitos básicos, vale a pena mencionar em relação a como você pode usar contêineres.

## <a name="container-equals-a-process"></a>Contêiner é igual a um processo

No modelo de contêiner, um contêiner representa um único processo. Definindo um contêiner como um limite de processo, você começar a criar os primitivos usados para escala, ou em lotes de lançamento, processos. Quando você executa um contêiner do Docker, você verá um [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definição. Isso define o processo e o tempo de vida do contêiner. Quando o processo for concluído, o ciclo de vida do contêiner será encerrada. Há processos de longa execução, como servidores web e processos de curta duração, como trabalhos de lote, que podem ter sido implementados como o Microsoft Azure [WebJobs](https://azure.microsoft.com/en-us/documentation/articles/websites-webjobs-resources/). Se o processo falhar, o contêiner é encerrado e o orquestrador assume. Se o orchestrator instruído para manter a cinco instâncias em execução e um falhar, o orchestrator criará outro contêiner para substituir o processo com falha. Em um trabalho em lotes, o processo é iniciado com parâmetros. Quando o processo é concluído, o trabalho é concluído.

Você pode encontrar um cenário no qual você deseja que vários processos em execução em um único contêiner. Em qualquer documento de arquitetura, nunca há um "nunca", nem sempre há um "sempre". Para cenários que exigem vários processos, um padrão comum é usar [Supervisor](http://supervisord.org/).


>[!div class="step-by-step"]
[Anterior] (design-docker-applications.md) [Avançar] (monolítico applications.md)
