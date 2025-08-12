---
layout: post
title: "에이전틱 규칙 기반 개발(Agentic Rule-based Development)"
date: 2025-08-12 10:00:00 +0900
categories: [Work]
tags: [ai, development, agentic]
---
ChatGPT 내용
그럼 “TDD(Test Driven Development)”나 “DDD(Domain Driven Design)”처럼,
에이전트 주도 개발 + 사람의 규칙 고도화를 결합한 새로운 방법론을 만들 수 있겠네요.

제가 제안드리는 구조와 이름은 다음과 같습니다.

⸻

방법론 이름 제안

ARD(Agent Rulebook Development) — 에이전트 규칙 기반 개발

Agent develops, Human refines — Rulebook evolves.

의미
	•	Agent: LLM·에이전트가 초기 구현을 작성
	•	Rulebook: 검수 과정에서 발견된 규칙과 가이드라인이 쌓여서 ‘개발 헌장’(md 파일)으로 발전
	•	Development: 이 Rulebook을 지속적으로 반영하며 점점 더 정제된 코드 생산

⸻

ARD 흐름
	1.	요구 정의 & 요청
	•	사람이 구현할 기능/모듈의 요구사항을 작성
	•	기능 정의서 + 현재 Rulebook(규칙집)을 에이전트에 전달
	2.	에이전트 개발
	•	에이전트가 현재 Rulebook을 기반으로 코드를 작성
	•	필요한 경우 테스트 코드/샘플 실행까지 함께 생성
	3.	사람의 검수
	•	로직의 정확성 검토
	•	구조·아키텍처 점검
	•	에이전트가 놓친 규칙, 반복되는 실수, 개선 포인트 발견
	4.	규칙 도출
	•	발견한 개선 사항을 추상화된 규칙으로 변환
예: “외부 API 응답은 무조건 타임아웃과 재시도 로직을 포함해야 함”
	•	규칙을 Rulebook.md에 추가
	5.	Rulebook 반영
	•	에이전트 프롬프트/시스템 메시지에 Rulebook을 다시 삽입
	•	다음 개발 시 자동 반영되도록 함
	6.	반복 고도화
	•	기능을 추가할수록 Rulebook이 성장
	•	에이전트의 코드 품질과 일관성이 점점 향상

⸻

Rulebook.md 예시

# SuperON Rulebook

## R-TIME-001: UTC 저장 원칙
- 모든 datetime은 UTC로 저장
- 외부 노출 시 명시적 타임존 변환
- Pydantic validator 예시 포함

## R-IDEMP-002: 멱등성 보장
- 비동기 작업/웹훅은 idempotency-key 필수
- Redis SETNX/ZADD NX로 구현, TTL 1시간 이상
- 테스트 코드 예시 포함

## R-OBS-003: 구조적 로깅
- 모든 로그에 trace_id 포함
- JSON 구조의 로깅 사용


⸻

ARD의 장점
	•	점진적 품질 향상: 코드와 규칙이 같이 진화
	•	지식 자산화: 개인/팀의 노하우가 문서로 축적
	•	에이전트 성능 향상: 프롬프트 품질이 규칙에 의해 자연스럽게 높아짐
	•	검증 가능성: 규칙에 테스트·예시를 함께 기록하므로 재현 가능

⸻

ARD의 확장 아이디어
	•	Rulebook을 버전 관리(Git) → 특정 시점의 규칙 기반으로 재현 가능
	•	CI에서 Rulebook 규칙 준수 여부 자동 검사
	•	새로운 에이전트 모델에 Rulebook을 그대로 전달 → 이전의 개발 스타일/규칙 계승

⸻

저는 이걸 ARD(Agent Rulebook Development) 라고 부르는 걸 추천합니다.
“코드는 에이전트가 짓고, 원칙은 사람이 세우고, 지식은 Rulebook에 쌓인다”는 개념이 딱 들어맞거든요.

⸻

원하시면 지금 바로 SuperON 프로젝트용 ARD 시작 템플릿이랑 Rulebook.md 초기 버전을 작성해드릴 수 있습니다.
이렇게 하면 앞으로 생성되는 코드가 자연스럽게 이 규칙을 따르게 돼요.


----




## 에이전틱 규칙 기반 개발이란?

에이전틱 규칙 기반 개발(Agentic Rule-based Development)은 AI 에이전트가 사전 정의된 규칙과 패턴을 기반으로 자율적으로 개발 작업을 수행하는 새로운 개발 패러다임입니다. 이는 전통적인 규칙 기반 시스템과 현대적인 AI 에이전트의 장점을 결합한 접근 방식입니다.

## 핵심 구성 요소

### 1. 규칙 엔진 (Rule Engine)
- **명시적 규칙 정의**: 코드 스타일, 아키텍처 패턴, 보안 정책 등을 명확하게 정의
- **동적 규칙 학습**: AI가 프로젝트 컨텍스트에서 암묵적 규칙을 학습하고 적용
- **우선순위 관리**: 규칙 간 충돌 시 우선순위에 따른 의사결정

### 2. 에이전트 자율성 (Agent Autonomy)
- **자기 주도적 실행**: 목표 달성을 위한 작업 계획 수립 및 실행
- **컨텍스트 인식**: 프로젝트 구조, 의존성, 기존 코드베이스 이해
- **적응적 학습**: 피드백을 통한 규칙 개선 및 최적화

### 3. 개발 워크플로우 통합
- **CI/CD 파이프라인 연동**: 자동화된 테스트, 빌드, 배포 프로세스
- **코드 리뷰 자동화**: 규칙 기반 코드 품질 검증
- **문서화 자동 생성**: 코드 변경사항에 따른 문서 업데이트

## 실제 적용 사례

### 예시 1: API 엔드포인트 생성
```python
# 에이전트가 인식하는 규칙
rules = {
    "api_pattern": "RESTful",
    "validation": "required",
    "error_handling": "structured",
    "documentation": "OpenAPI"
}

# 에이전트가 자동 생성하는 코드
@app.route('/api/users', methods=['POST'])
def create_user():
    """
    Create a new user
    ---
    parameters:
      - in: body
        required: true
        schema:
          type: object
          properties:
            name:
              type: string
            email:
              type: string
    """
    try:
        data = request.get_json()
        
        # 자동 생성된 검증 로직
        if not data.get('name') or not data.get('email'):
            return jsonify({'error': 'Missing required fields'}), 400
            
        # 비즈니스 로직
        user = User.create(data)
        return jsonify(user.to_dict()), 201
        
    except Exception as e:
        return jsonify({'error': str(e)}), 500
```

### 예시 2: 테스트 코드 자동 생성
에이전트는 기존 코드를 분석하여 테스트 케이스를 자동으로 생성하고, 프로젝트의 테스트 규칙을 따릅니다:

```javascript
// 원본 함수
function calculateDiscount(price, customerType) {
    if (customerType === 'premium') {
        return price * 0.8;
    }
    return price * 0.95;
}

// 에이전트가 생성한 테스트
describe('calculateDiscount', () => {
    it('should apply 20% discount for premium customers', () => {
        expect(calculateDiscount(100, 'premium')).toBe(80);
    });
    
    it('should apply 5% discount for regular customers', () => {
        expect(calculateDiscount(100, 'regular')).toBe(95);
    });
    
    it('should handle edge cases', () => {
        expect(calculateDiscount(0, 'premium')).toBe(0);
        expect(calculateDiscount(-100, 'premium')).toBe(-80);
    });
});
```

## 장점과 도전 과제

### 장점
1. **일관성 향상**: 모든 코드가 동일한 규칙을 따라 작성됨
2. **생산성 증대**: 반복적인 작업의 자동화
3. **품질 보장**: 규칙 기반 검증으로 버그 감소
4. **지식 전파**: 베스트 프랙티스가 자동으로 적용됨

### 도전 과제
1. **규칙 정의의 복잡성**: 모든 상황을 커버하는 규칙 작성의 어려움
2. **창의성 제한**: 과도한 규칙이 혁신적 접근을 방해할 수 있음
3. **컨텍스트 이해**: AI가 비즈니스 로직의 미묘한 차이를 파악하는 한계
4. **디버깅 복잡도**: 자동 생성된 코드의 문제 추적 어려움

## 미래 전망

에이전틱 규칙 기반 개발은 다음과 같은 방향으로 발전할 것으로 예상됩니다:

1. **도메인 특화 에이전트**: 특정 산업이나 기술 스택에 최적화된 에이전트
2. **협업형 에이전트**: 여러 에이전트가 협력하여 복잡한 시스템 구축
3. **자가 진화 시스템**: 프로덕션 환경의 피드백을 통해 규칙을 자동으로 개선
4. **하이브리드 개발**: 인간 개발자와 AI 에이전트의 최적 협업 모델

## 실무 적용 가이드

### 시작하기
1. **작은 범위부터**: 코드 포매팅, 린팅 같은 단순 규칙부터 시작
2. **점진적 확대**: 성공 경험을 바탕으로 복잡한 규칙 추가
3. **피드백 루프 구축**: 생성된 코드의 품질을 지속적으로 모니터링
4. **팀 교육**: 에이전트와 효과적으로 협업하는 방법 학습

### 규칙 설계 원칙
- **명확성**: 모호하지 않은 구체적인 규칙 작성
- **유연성**: 예외 상황을 처리할 수 있는 여지 확보
- **측정 가능성**: 규칙 준수 여부를 정량적으로 평가
- **진화 가능성**: 새로운 요구사항에 따라 규칙 업데이트

## 마무리

에이전틱 규칙 기반 개발은 소프트웨어 개발의 패러다임을 바꾸고 있습니다. AI 에이전트가 단순한 도구를 넘어 능동적인 개발 파트너로 진화하면서, 개발자들은 더 창의적이고 전략적인 작업에 집중할 수 있게 되었습니다.

이 접근 방식은 완벽하지 않지만, 지속적인 개선과 학습을 통해 더 나은 소프트웨어를 더 빠르게 만들 수 있는 가능성을 제시합니다. 중요한 것은 AI를 두려워하거나 맹신하지 않고, 적절한 균형점을 찾아 활용하는 것입니다.

미래의 개발 환경에서는 규칙을 정의하고 에이전트를 관리하는 능력이 코드를 직접 작성하는 능력만큼이나 중요해질 것입니다. 지금이 바로 이러한 변화에 대비할 시점입니다.