<picture class="github-only">
  <source media="(prefers-color-scheme: light)" srcset="https://langchain-ai.github.io/langgraph/static/wordmark_dark.svg">
  <source media="(prefers-color-scheme: dark)" srcset="https://langchain-ai.github.io/langgraph/static/wordmark_light.svg">
  <img alt="LangGraph 로고" src="https://langchain-ai.github.io/langgraph/static/wordmark_dark.svg" width="80%">
</picture>

<div>
<br>
</div>

[![Version](https://img.shields.io/pypi/v/langgraph.svg)](https://pypi.org/project/langgraph/)
[![Downloads](https://static.pepy.tech/badge/langgraph/month)](https://pepy.tech/project/langgraph)
[![Open Issues](https://img.shields.io/github/issues-raw/langchain-ai/langgraph)](https://github.com/langchain-ai/langgraph/issues)
[![Docs](https://img.shields.io/badge/docs-latest-blue)](https://langchain-ai.github.io/langgraph/)

Klarna, Replit, Elastic 등을 포함한 에이전트 분야의 선도 기업들이 신뢰하는 LangGraph는 장시간 실행되는 상태 기반 에이전트를 구축하고 관리하며 배포하기 위한 저수준 오케스트레이션 프레임워크입니다.

## 시작하기

LangGraph 설치:

```
pip install -U langgraph
```

그런 다음 [미리 구축된 컴포넌트](https://langchain-ai.github.io/langgraph/agents/agents/)를 이용해 에이전트를 만듭니다:

```python
# 모델 호출을 위해 "langchain[anthropic]" 패키지를 설치하세요

from langgraph.prebuilt import create_react_agent

def get_weather(city: str) -> str:
    """주어진 도시의 날씨를 가져옵니다."""
    return f"{city}의 날씨는 언제나 맑습니다!"

agent = create_react_agent(
    model="anthropic:claude-3-7-sonnet-latest",
    tools=[get_weather],
    prompt="당신은 도움이 되는 어시스턴트입니다"
)

# 에이전트 실행
agent.invoke(
    {"messages": [{"role": "user", "content": "what is the weather in sf"}]}
)
```

자세한 내용은 [빠른 시작](https://langchain-ai.github.io/langgraph/agents/agents/)을 참조하세요. 맞춤형 아키텍처와 장기 메모리 등 복잡한 작업을 처리하는 [에이전트 워크플로우](https://langchain-ai.github.io/langgraph/concepts/low_level/)를 구축하는 방법은 [LangGraph 기본 튜토리얼](https://langchain-ai.github.io/langgraph/tutorials/get-started/1-build-basic-chatbot/)을 살펴보세요.

## 핵심 장점

LangGraph는 *어떤* 장시간 실행되는 상태 기반 워크플로우나 에이전트에도 사용 가능한 저수준 인프라를 제공합니다. 프롬프트나 아키텍처를 추상화하지 않으며, 다음과 같은 주요 이점을 제공합니다:

- [내구성 있는 실행](https://langchain-ai.github.io/langgraph/concepts/durable_execution/): 실패 후에도 중단된 지점에서 정확히 이어서 실행될 수 있도록 장기간 동작하는 에이전트를 구축합니다.
- [휴먼 인 더 루프](https://langchain-ai.github.io/langgraph/concepts/human_in_the_loop/): 실행 중 언제든지 에이전트 상태를 검사하고 수정하여 사람의 개입을 매끄럽게 통합합니다.
- [포괄적인 메모리](https://langchain-ai.github.io/langgraph/concepts/memory/): 지속적인 세션 간 장기 메모리와 현재 추론을 위한 단기 워킹 메모리를 모두 갖춘 진정한 상태 기반 에이전트를 만듭니다.
- [LangSmith로 디버깅](http://www.langchain.com/langsmith): 실행 경로와 상태 변화를 추적하고 자세한 런타임 메트릭을 제공하는 시각화 도구로 복잡한 에이전트 동작을 깊이 있게 파악합니다.
- [프로덕션 준비된 배포](https://langchain-ai.github.io/langgraph/concepts/deployment_options/): 상태 기반의 장기 워크플로우가 지니는 고유한 과제를 처리할 수 있도록 설계된 확장 가능한 인프라로 복잡한 에이전트 시스템을 자신 있게 배포합니다.

## LangGraph 생태계

LangGraph는 단독으로도 사용할 수 있지만, LangChain 제품군과 매끄럽게 통합되어 에이전트 구축을 위한 완전한 도구 세트를 제공합니다. LLM 애플리케이션 개발을 향상시키려면 LangGraph를 다음과 함께 사용하세요:

- [LangSmith](http://www.langchain.com/langsmith) — 에이전트 평가와 가시성에 유용합니다. 성능이 떨어지는 LLM 실행을 디버깅하고, 에이전트 경로를 평가하며, 프로덕션에서의 가시성을 확보하여 성능을 향상시킵니다.
- [LangGraph Platform](https://langchain-ai.github.io/langgraph/concepts/#langgraph-platform) — 장시간 실행되는 상태 기반 워크플로우를 위한 전용 배포 플랫폼으로 에이전트를 손쉽게 배포하고 확장합니다. [LangGraph Studio](https://langchain-ai.github.io/langgraph/concepts/langgraph_studio/)의 시각적 프로토타이핑으로 빠르게 반복하고, 팀 내에서 에이전트를 발견·재사용·구성·공유하세요.
- [LangChain](https://python.langchain.com/docs/introduction/) – LLM 애플리케이션 개발을 간소화하는 통합 및 구성 요소를 제공합니다.

> [!NOTE]
> LangGraph의 JS 버전을 찾고 계신가요? [JS 저장소](https://github.com/langchain-ai/langgraphjs)와 [JS 문서](https://langchain-ai.github.io/langgraphjs/)를 확인하세요.

## 추가 자료

- [가이드](https://langchain-ai.github.io/langgraph/how-tos/): 스트리밍, 메모리 및 지속성 추가, 분기나 서브그래프와 같은 디자인 패턴 등 주제별로 바로 사용할 수 있는 코드 조각을 제공합니다.
- [레퍼런스](https://langchain-ai.github.io/langgraph/reference/graphs/): 그래프와 체크포인팅 API 사용법, 상위 수준의 프리빌트 컴포넌트 등 핵심 클래스와 메서드에 대한 상세 정보를 제공합니다.
- [예제](https://langchain-ai.github.io/langgraph/tutorials/overview/): LangGraph 사용을 시작하는 방법을 안내하는 예제입니다.
- [LangChain 아카데미](https://academy.langchain.com/courses/intro-to-langgraph): 무료로 제공되는 구조화된 강의에서 LangGraph의 기본을 배워보세요.
- [템플릿](https://langchain-ai.github.io/langgraph/concepts/template_applications/): ReAct 에이전트, 메모리, 검색 등 일반적인 에이전트 워크플로우를 위한 사전 구축 레퍼런스 앱을 복제하여 사용할 수 있습니다.
- [사례 연구](https://www.langchain.com/built-with-langgraph): 산업 리더들이 LangGraph를 활용해 어떻게 대규모 AI 애플리케이션을 출시했는지 확인하세요.

## 감사의 글

LangGraph는 [Pregel](https://research.google/pubs/pub37252/)과 [Apache Beam](https://beam.apache.org/)에서 영감을 받았습니다. 공용 인터페이스는 [NetworkX](https://networkx.org/documentation/latest/)에서 아이디어를 얻었으며, LangGraph는 LangChain의 제작사인 LangChain Inc에서 개발했지만 LangChain 없이도 사용할 수 있습니다.
