**Volume 11. Physical AI Evaluation and Benchmarking**

# Chapter 06. Long Horizon Task Evaluation

## 06.01. Why Long Horizon Evaluation Matters

![](images/image1.png){width="7.268055555555556in" height="7.268055555555556in"}

장기 작업 평가(Long-Horizon Task Evaluation)는 피지컬 인공지능(Physical AI) 시스템이 장기간에 걸친 의사결정(Decision-Making), 행동(Action), 환경 상호작용(Environmental Interaction)의 연속적인 과정에서 성공적으로 작동해야 하기 때문에 필수적이다. 개별적인 움직임이나 조작 기술(Manipulation Skill)을 수행하는 능력만으로는 복잡한 임무(Mission)를 완수할 수 있음을 입증할 수 없다. 실제 환경에서의 자율성(Autonomy)은 이전의 결정이 이후의 기회, 제약 조건 및 결과에 영향을 미치는 시간적 연속성 속에서 조정된 실행 능력을 요구한다.

전통적인 벤치마크(Benchmark)는 명확하게 정의된 초기 상태(Initial State)와 즉각적인 성공 조건(Success Condition)을 갖는 단기 작업(Short-Duration Task)에 중점을 두는 경우가 많다. 이러한 평가는 개별 역량(Capability)을 측정하는 데 유용하지만 지속적인 자율성(Sustained Autonomy)을 입증하는 데에는 한계가 있다. 로봇이 객체 인식(Object Recognition), 내비게이션(Navigation), 파지(Grasping)에서 각각 우수한 성능을 보이더라도 이러한 역량을 결합하여 신뢰할 수 있는 운영 작업 흐름(Operational Workflow)을 수행하는 데 실패할 수 있다.

장기 작업(Long-Horizon Task)은 개별 성공률(Success Rate)만으로 충분히 평가할 수 없는 행동 간 의존성(Action Dependency)을 포함한다. 창고 로봇(Warehouse Robot)은 재고를 찾고, 여러 통로를 이동하며, 물체를 조작하고, 자재를 운반한 다음 배송 완료 여부를 검증해야 할 수 있다. 각 단계는 이전 단계의 성공적인 완료에 의존하며, 초기 작업에서 발생한 오류(Error)는 전체 임무가 의도한 목표에 도달하지 못하게 만들 수 있다.

장기 작업 평가의 중요성은 오류 누적(Compounding Error)을 고려할 때 더욱 분명해진다. 개별 행동의 성공 확률(Success Probability)이 높더라도 긴 행동 시퀀스(Action Sequence)를 오류 없이 완료할 확률은 크게 감소할 수 있다. 서로 독립적인 20개의 행동이 각각 0.98의 성공 확률을 갖는다면 전체 20개 행동이 모두 성공할 확률은 약 0.668이다. 이는 우수한 단기 성능(Short-Horizon Performance)이 반드시 임무 신뢰성(Mission Reliability)을 보장하지 않음을 보여준다.

그러나 실제 로봇 작업은 동일한 성공 확률을 갖는 독립적인 행동으로 구성되는 경우가 드물다. 환경 조건(Environmental Condition), 누적된 불확실성(Accumulated Uncertainty), 이전 의사결정 및 시스템 성능 저하(System Degradation)는 실패 간 상관관계(Correlation)를 발생시킨다. 따라서 장기 작업 평가는 단순화된 확률 계산에만 의존하지 않고 인식(Perception), 계획(Planning), 제어(Control), 상호작용(Interaction) 전반에서 오류가 어떻게 전파되는지 분석해야 한다.

또 다른 근본적인 과제는 장기간의 작업 수행 과정에서 정확한 세계 표현(World Representation)을 유지하는 것이다. 물체가 이동하고, 사람이 개입하며, 로봇이 주변 환경을 변경함에 따라 물리적 환경(Physical Environment)은 지속적으로 변화한다. 초기에는 정확한 장면 표현(Scene Representation)을 구축한 시스템도 시간이 지나면서 불일치가 누적될 수 있다. 장기 역량(Long-Horizon Competence)을 평가하려면 내부 세계 상태(Internal World State)가 관측 가능한 물리적 조건과 지속적으로 일치하는지 확인해야 한다.

작업 시간이 길어질수록 기억(Memory)과 문맥 유지(Context Retention)도 중요해진다. 로봇은 이전에 검사한 위치, 완료된 하위 작업(Subtask), 물체의 식별 정보(Object Identity), 운영 제약 조건(Operational Constraint), 사용자 명령(User Instruction)을 기억해야 할 수 있다. 관련 정보를 잃으면 중복 행동, 잘못된 의사결정 또는 안전하지 않은 동작이 발생할 수 있다. 장기 작업 평가는 시스템이 유용한 문맥을 유지하면서 오래된 정보를 적절하게 갱신하는지 확인한다.

계획 품질(Planning Quality)은 로봇이 유효한 초기 행동 시퀀스를 생성하는지만으로 평가할 수 없다. 장기 임무(Extended Mission)는 기존 가정이 유효하지 않게 되었을 때 지속적인 모니터링(Monitoring), 적응(Adaptation), 재계획(Replanning)을 요구한다. 장애물이 나타나거나 자원을 사용할 수 없게 되고 작업 우선순위가 변경될 수 있다. 유능한 피지컬 인공지능 시스템은 원래 목표를 향한 진행 상황을 불필요하게 포기하지 않으면서 전략을 수정해야 한다.

장기 작업 평가는 정상적인 작업 실행(Nominal Task Execution)과 회복력 있는 자율 행동(Resilient Autonomous Behavior)을 구분한다. 모든 작업이 예상대로 진행될 때만 임무를 완수하는 로봇은 실제 활용 가치가 제한적이다. 실제 배포 환경(Real-World Deployment)에서는 예상하지 못한 접촉, 위치 추정 불확실성(Localization Uncertainty), 일시적인 통신 장애(Communication Failure), 조작 오류(Manipulation Error)가 발생한다. 따라서 로봇이 이상 상태를 감지하고, 그 결과를 진단하며, 의미 있는 작업 진행 상태를 복구할 수 있는지 평가해야 한다.

실패 복구(Failure Recovery)는 일시적인 문제(Temporary Setback)와 최종적인 임무 실패(Terminal Mission Failure)를 구분하는 중요한 기준이다. 로봇이 물체를 떨어뜨리더라도 안전하게 위치를 파악하고 다시 집을 수 있다면 배송 작업이 반드시 실패한 것은 아니다. 마찬가지로 내비게이션 시도에 실패하더라도 경로 수정(Route Modification)을 통해 복구할 수 있다. 평가는 모든 중간 실패를 최종 실패로 처리하기보다 복구의 효과성(Effectiveness), 비용(Cost), 안전성(Safety)을 측정해야 한다.

인간 개입(Human Intervention)은 지속적인 자율성(Sustained Autonomy)을 평가하는 또 다른 중요한 요소이다. 로봇이 빈번한 운영자 지원(Operator Assistance), 수동 재설정(Manual Reset), 수정 지시(Corrective Instruction)를 받아 임무를 완료할 수도 있다. 최종 결과는 성공으로 나타나지만 운영 부담(Operational Burden)은 여전히 클 수 있다. 장기 벤치마크는 개입 빈도(Intervention Frequency), 개입 시간(Intervention Duration), 지원 유형(Assistance Type), 외부 지원이 임무 완료에 기여한 정도를 기록해야 한다.

자율 운영 시간(Autonomy Duration)은 시스템 역량에 대한 보완적인 정보를 제공한다. 로봇이 외부 지원 없이 얼마나 오랫동안 작동하는지 측정하면 단기 시험(Short Trial)에서 발견하지 못한 한계를 확인할 수 있다. 개입 간 평균 시간(Mean Time Between Interventions)은 운영 성숙도(Operational Maturity)를 나타낼 수 있지만, 그 해석은 작업 난이도(Task Difficulty)와 환경 노출(Environmental Exposure)에 따라 달라진다. 이러한 측정값은 임무 성공, 안전성, 실행 품질과 함께 분석할 때 더욱 의미가 있다.

장시간 운영(Extended Operation)은 하드웨어(Hardware)와 소프트웨어(Software)의 통합과 관련된 신뢰성 문제도 드러낸다. 센서 드리프트(Sensor Drift), 액추에이터 발열(Actuator Heating), 배터리 방전(Battery Discharge), 컴퓨팅 자원 제약(Computational Resource Constraint)이 발생할 수 있다. 짧은 시연에서 효과적으로 작동하던 제어 정책(Control Policy)도 장시간 운영 후에는 다른 행동을 보일 수 있다. 따라서 장기 작업 평가는 인공지능 모델만이 아니라 통합된 피지컬 인공지능 시스템 전체를 검증한다.

시간적 기여도 할당(Temporal Credit Assignment)은 최종 임무 결과가 훨씬 이전에 이루어진 결정에 영향을 받을 수 있기 때문에 또 다른 과제가 된다. 준비 단계에서 비효율적으로 물체를 배치한 결정이 몇 분 후 조작 실패(Manipulation Failure)를 유발할 수 있다. 평가자는 전체 궤적(Trajectory)에 걸쳐 어떤 결정이 성공이나 실패에 기여했는지 식별해야 한다. 이를 위해 중간 관측(Intermediate Observation), 행동(Action), 상태 전이(State Transition), 의미 있는 작업 이정표(Task Milestone)를 보존해야 한다.

임무에 여러 하위 작업(Subtask)이 포함되어 있다면 중간 진행 상황(Intermediate Progress)의 평가가 특히 중요하다. 이진 완료 지표(Binary Completion Metric)는 전체 결과를 명확하게 제공하지만 시스템 간 중요한 차이를 감출 수 있다. 어떤 로봇은 즉시 실패하는 반면 다른 로봇은 복구 가능한 장애물을 만나기 전까지 거의 모든 단계를 완료할 수 있다. 진행 상황 기반 평가(Progress-Aware Evaluation)는 부분적인 성취(Partial Achievement)를 전체 임무 성공과 혼동하지 않으면서 이러한 행동 차이를 구분하도록 돕는다.

장기 벤치마크는 효율성(Efficiency)과 신뢰성(Reliability)의 관계도 고려해야 한다. 로봇은 실행 시간을 늘리더라도 충돌 위험(Collision Risk)과 복구 요구 사항(Recovery Requirement)을 줄이는 보수적인 전략(Conservative Strategy)을 선택할 수 있다. 반면 다른 시스템은 유리한 조건에서 빠르게 작업을 완료하지만 외란(Disturbance)이 발생하면 빈번하게 실패할 수 있다. 의미 있는 평가는 완료 시간(Completion Time), 에너지 소비(Energy Consumption), 개입 비용(Intervention Cost), 안전성, 임무 성공을 종합적으로 고려한다.

환경 다양성(Environmental Diversity)은 장기 시험(Long-Horizon Testing)의 중요성을 더욱 높인다. 장기 임무는 개별 실험에서 나타나지 않을 수 있는 다양한 조건의 조합에 로봇을 노출시킨다. 조명 변화(Lighting Change), 인간 활동(Human Activity), 이동 장애물(Moving Obstacle), 물체 재배치(Object Rearrangement), 표면 변화(Surface Variation)는 시간에 따라 상호작용할 수 있다. 평가는 시스템이 고정된 초기 구성뿐 아니라 변화하는 조건에서도 역량을 유지하는지 확인해야 한다.

시뮬레이션(Simulation)과 실제 환경 시험(Real-World Testing)의 차이는 장기 작업에서 특히 중요해진다. 시뮬레이션은 반복 실험(Repeated Experiment), 제어된 외란(Controlled Disturbance), 상세한 궤적 분석(Trajectory Analysis)을 가능하게 하므로 체계적인 약점을 식별하는 데 유용하다. 그러나 시뮬레이션 환경은 누적된 기계적 영향(Mechanical Effect), 센서 성능 저하(Sensor Degradation), 예측하기 어려운 인간 상호작용(Human Interaction)을 충분히 반영하지 못할 수 있다. 따라서 운영 타당성(Operational Validity)을 확립하려면 실제 환경 시험이 필요하다.

재현성(Reproducibility)을 확보하려면 임무 목표(Mission Objective), 초기 조건(Initial Condition), 환경 변동성(Environmental Variability), 종료 규칙(Termination Rule), 허용되는 개입(Permitted Intervention)을 명확하게 정의해야 한다. 일관된 평가 절차(Evaluation Protocol)가 없다면 작업 시간이나 난이도의 차이가 시스템 간 비교를 왜곡할 수 있다. 장기 작업 평가는 통계적으로 의미 있는 결론을 지원하기 위해 반복 시험(Multiple Trial), 결과 분포(Outcome Distribution), 실패 유형(Failure Category), 불확실성 추정(Uncertainty Estimate)을 보고해야 한다.

또 다른 우려 사항은 벤치마크 과적합(Benchmark Overfitting)이다. 이는 시스템이 전이 가능한 자율성(Transferable Autonomy)을 개발하기보다 예측 가능한 작업 시퀀스를 활용하도록 학습하는 현상이다. 동일한 물체 배치, 내비게이션 경로, 사전에 작성된 외란(Scripted Disturbance)에 반복적으로 노출되면 진정한 적응 능력(Adaptability)을 입증하지 못하면서도 우수한 결과를 얻을 수 있다. 따라서 평가는 비교 가능한 난이도를 유지하면서 처음 접하는 작업 조합(Unseen Task Composition), 변화하는 환경, 대안적인 실행 경로(Alternative Execution Pathway)를 포함해야 한다.

궁극적으로 장기 작업 평가(Long-Horizon Task Evaluation)는 피지컬 인공지능(Physical AI)이 개별 역량을 신뢰할 수 있는 임무 수준 자율성(Mission-Level Autonomy)으로 전환할 수 있는지 측정한다. 그 목적은 이상적인 조건에서 로봇이 복잡한 행동 시퀀스를 수행할 수 있음을 보여주는 데 그치지 않는다. 지속적인 물리적 운영(Sustained Physical Operation) 전반에서 상황 인식(Situational Awareness)을 유지하고, 불확실성(Uncertainty)을 관리하며, 실패로부터 복구하고, 인간의 지원을 최소화하면서 목표를 일관되게 달성할 수 있는지를 검증하는 데 있다.

## 06.02. From Atomic Skills to Complete Missions

![](images/image2.png){width="7.268055555555556in" height="7.268055555555556in"}

원자적 기술(Atomic Skills)은 로봇이 환경을 인식하고, 의사결정을 수행하며, 행동하는 데 필요한 물리적 지능(Physical Intelligence)의 기본 단위를 나타낸다. 대표적인 예로는 객체 감지(Object Detection), 목표 지점 도달(Reaching), 부품 파지(Grasping), 경유점 이동(Waypoint Navigation), 장애물 회피(Obstacle Avoidance)가 있다. 이러한 역량은 독립적으로 평가할 수 있지만, 여러 목표와 의존성을 포함하는 완전한 임무(Complete Mission)로 조정되고 통합될 때 실질적인 가치가 나타난다.

완전한 임무(Complete Mission)는 서로 연결된 활동의 연속적인 과정에서 로봇이 일관된 목표(Coherent Objective)를 유지해야 한다는 점에서 개별 기술(Isolated Skill)과 구별된다. 창고 배송 임무(Warehouse Delivery Mission)는 물품 식별, 보관 위치로의 이동, 물품 회수, 공동 작업 공간을 통한 운송, 배송 완료 확인을 포함할 수 있다. 최종 결과는 개별 기술의 성능뿐 아니라 연속적인 작업 사이의 올바른 조정(Coordination)에 의해서도 결정된다.

원자적 기술에서 완전한 임무로 전환하는 과정에서는 계층적 작업 구성(Hierarchical Task Organization)이 도입된다. 상위 수준 목표(High-Level Goal)는 중간 목표(Intermediate Objective), 실행 가능한 하위 작업(Executable Subtask), 하위 수준 제어 행동(Low-Level Control Action)으로 분해된다. 작업 공간을 준비하는 로봇은 먼저 필요한 도구를 식별하고, 자재를 가져오며, 물체를 배치한 다음 준비 상태를 검증할 수 있다. 평가는 시스템이 적절한 하위 작업을 선택하고 논리적으로 일관된 순서로 실행하는지 확인해야 한다.

기술 조합(Skill Composition)은 개별 시험(Isolated Testing)에서는 드러나지 않는 문제를 발생시킨다. 독립적으로 신뢰성이 높은 두 기술도 환경에 대한 가정이 서로 다르면 연속 실행 과정에서 실패할 수 있다. 파지 정책(Grasping Policy)은 물체가 특정 방향으로 놓여 있다고 가정하지만, 이전의 내비게이션 또는 위치 조정 작업이 다른 배치를 만들어낼 수 있다. 임무 수준 평가(Mission-Level Evaluation)는 기술 간 전환이 성공적인 실행에 필요한 조건을 유지하는지 확인한다.

사전 조건(Precondition)과 사후 조건(Postcondition)은 이러한 의존성을 분석하는 데 유용한 체계를 제공한다. 조작 행동(Manipulation Action)은 로봇이 도달 가능한 거리(Reachable Distance)에 위치하고, 충분한 파지 여유 공간(Grasp Clearance)을 확보하며, 안정적인 베이스 구성(Stable Base Configuration)을 유지해야 할 수 있다. 성공적인 실행은 환경에서 검증 가능한 변화를 만들어야 한다. 이러한 조건의 충족 여부를 평가하면 개별 기술의 결함이 아니라 잘못된 작업 순서(Incorrect Sequencing)에서 발생한 실패를 식별할 수 있다.

임무 실행(Mission Execution)에는 진행 상황에 대한 지속적인 표현(Persistent Representation)도 필요하다. 로봇은 관련 환경 변화를 인식하면서 완료된 하위 작업과 대기 중인 작업(Pending Operation)을 구분해야 한다. 신뢰할 수 있는 진행 상황 추적(Progress Tracking)이 없다면 시스템은 행동을 반복하거나 필요한 단계를 생략하거나 작업을 조기에 종료할 수 있다. 평가는 로봇이 실행 과정 전반에서 정확한 작업 상태(Task State)를 유지하고 관측 결과가 이전 가정과 모순될 때 이를 갱신하는지 확인해야 한다.

시간적 의존성(Temporal Dependency)은 기술 조합을 더욱 복잡하게 만든다. 특정 행동은 다른 행동보다 먼저 수행해야 하지만, 일부 작업은 동시에 수행하거나 다른 순서로 실행할 수 있다. 이동형 매니퓰레이터(Mobile Manipulator)는 이동하기 전에 물체를 안정적으로 고정해야 할 수 있지만, 검사 작업(Inspection Task)은 유연한 작업 순서를 허용할 수 있다. 임무 평가는 시스템이 필수 제약 조건(Necessary Constraint)을 준수하면서 허용 가능한 유연성을 활용하여 효율성과 신뢰성을 향상시키는지 평가해야 한다.

장기 임무(Long-Horizon Mission)는 서로 다른 시간적 규모(Temporal Scale)에서 인식(Perception), 추론(Reasoning), 계획(Planning), 제어(Control)의 조정을 요구하는 경우가 많다. 하위 수준 제어기(Low-Level Controller)는 즉각적인 물리적 외란(Physical Disturbance)에 대응하지만, 상위 수준 계획기(High-Level Planner)는 수분 또는 수시간에 걸친 목표를 관리한다. 중간 의사결정 메커니즘(Intermediate Decision Mechanism)은 이러한 과정을 연결한다. 평가는 계층 간 정보가 효과적으로 전달되고 지역적 행동(Local Action)이 전체 임무 요구 사항과 일치하는지 확인해야 한다.

원자적 기술 벤치마크(Atomic Skill Benchmark)의 주요 한계는 세심하게 준비된 초기 조건(Initial Condition)에 의존한다는 점이다. 파지 시험에서는 물체를 로봇의 도달 범위 안에 배치하고, 내비게이션 시험에서는 알려진 시작 자세(Starting Pose)를 제공할 수 있다. 그러나 완전한 임무에서는 이러한 편리한 조건이 거의 제공되지 않는다. 로봇은 필요한 조건을 스스로 구축해야 하므로 자율적 준비(Autonomous Preparation)와 상태 추정(State Estimation)이 임무 수준 역량(Mission-Level Competence)의 필수 요소가 된다.

기술 실행(Skill Execution)은 후속 작업에 영향을 미치는 방식으로 환경을 변화시킬 수도 있다. 컨테이너를 이동하면 다른 물체가 드러나거나 통로가 막히거나 사용 가능한 조작 공간(Manipulation Space)이 달라질 수 있다. 이러한 결과는 로봇의 세계 모델(World Model)을 지속적으로 갱신할 것을 요구한다. 임무 수준 평가는 시스템이 관련 변화를 예측하고 이전 결정으로 형성된 물리적 상태(Physical State)에 맞추어 후속 행동을 조정하는지 확인한다.

개별 하위 작업에서 발생한 실패가 자동으로 전체 임무 실패(Mission Failure)를 의미해서는 안 된다. 로봇은 파지에 실패한 후 접근 방식을 조정하거나 대체 조작 전략(Alternative Manipulation Strategy)을 선택하여 복구할 수 있다. 그러나 반복적인 복구 시도(Recovery Attempt)는 시간, 에너지, 운영 자원을 소비할 수 있다. 따라서 평가는 복구 가능한 기술 실패(Recoverable Skill Failure)와 최종 임무 실패(Terminal Mission Failure)를 구분하면서 수정 행동(Corrective Behavior)의 효과성과 비용을 측정해야 한다.

원자적 기술 성공률(Atomic Skill Success Rate)과 임무 완료 확률(Mission Completion Probability)의 관계는 특히 중요하다. 단순화된 독립성 가정(Independence Assumption)에서 각각 0.99의 성공 확률을 갖는 30개의 필수 기술로 구성된 임무의 전체 무중단 성공 확률(Uninterrupted Success Probability)은 약 0.74이다. 실제 시스템에서는 상관된 오류(Correlated Error)와 복구 메커니즘(Recovery Mechanism)이 존재하지만, 이 사례는 높은 구성 요소 수준 정확도(Component-Level Accuracy)가 반드시 신뢰할 수 있는 임무 수준 자율성(Mission-Level Autonomy)으로 이어지지 않음을 보여준다.

따라서 임무 수준 성능(Mission-Level Performance)은 이진 완료 지표(Binary Completion Indicator) 이상의 정보를 포함해야 한다. 유용한 측정 항목에는 하위 작업 완료(Subtask Completion), 작업 순서의 정확성(Sequencing Correctness), 실행 시간(Execution Time), 자원 소비(Resource Consumption), 복구 빈도(Recovery Frequency), 개입 요구 사항(Intervention Requirement), 최종 목표 충족(Final Objective Satisfaction)이 포함된다. 이러한 측정값은 로봇이 목표를 효율적이고 독립적으로 달성하는지, 아니면 반복적인 수정과 유리한 환경 조건에 의존하는지를 보여준다.

평가 프레임워크(Evaluation Framework)는 로봇이 학습된 기술을 다양한 임무 구성(Mission Configuration)에서 재사용할 수 있는지도 검토해야 한다. 동일한 내비게이션, 파지, 배치 기술은 창고 물류(Warehouse Logistics), 실험실 자동화(Laboratory Automation), 서비스 로보틱스(Service Robotics)에 활용될 수 있다. 그러나 성공적인 전이(Transfer)를 위해서는 기술 매개변수(Skill Parameter), 작업 순서 제약 조건(Ordering Constraint), 환경 가정(Environmental Assumption)을 조정해야 한다. 다양한 조합을 시험하면 시스템이 암기된 절차(Memorized Procedure)가 아니라 조합적 역량(Compositional Competence)을 갖추었는지 판단할 수 있다.

임무 복잡도(Mission Complexity)를 점진적으로 높이는 것은 역량의 경계(Capability Boundary)를 체계적으로 측정하는 방법이다. 평가자는 익숙한 기술의 짧은 시퀀스에서 시작하여 추가 하위 작업, 분기 의사결정(Branching Decision), 환경 변화, 지연된 의존성(Delayed Dependency)을 점진적으로 도입할 수 있다. 이러한 조건에서 나타나는 성능 저하(Performance Degradation)는 계획, 기억, 조정, 복구 능력의 한계를 드러낸다. 이러한 평가는 가장 어려운 임무만 시험하는 것보다 더 많은 진단 정보(Diagnostic Information)를 제공한다.

완전한 임무는 목표 검증(Goal Verification)에 대한 요구 사항도 도입한다. 계획된 모든 행동을 실행했다고 해서 반드시 의도한 목표를 달성한 것은 아니다. 로봇은 물체를 잘못된 목적지에 배치하거나 발견되지 않은 결함(Undetected Defect)이 있는 상태로 조립 시퀀스(Assembly Sequence)를 완료할 수 있다. 따라서 임무 평가는 적절한 관측(Observation), 측정(Measurement), 승인 기준(Acceptance Criteria)을 사용하여 절차적 실행(Procedural Execution)과 검증된 물리적 결과(Verified Physical Outcome)를 구분해야 한다.

자율 임무(Autonomous Mission)로의 전환을 평가할 때는 인간 지원(Human Assistance)을 명시적으로 표현해야 한다. 운영자는 지시를 제공하고, 위치 추정(Localization)을 수정하며, 조작 실패를 해결하거나 예외적인 행동(Exceptional Action)을 승인할 수 있다. 이러한 개입은 안전한 운영을 지원할 수 있지만 임무 성공의 해석을 변화시킨다. 평가 절차(Evaluation Protocol)는 지원의 허용 범위(Assistance Boundary)를 문서화하고 자율 완료(Autonomous Completion)와 지원을 받은 완료(Assisted Completion)를 구분하여 보고해야 한다.

안전 제약 조건(Safety Constraint)은 기술 조합 전반에서 필수적으로 유지되어야 한다. 개별적으로 안전한 행동의 시퀀스도 누적 효과(Cumulative Effect)나 변화하는 주변 환경을 고려하지 않고 실행하면 위험한 결과를 초래할 수 있다. 예를 들어 불완전한 파지(Imperfect Grasp) 이후 불안정한 하중(Unstable Load)을 운반하면 개별 시험에서는 존재하지 않았던 위험(Hazard)이 발생할 수 있다. 임무 수준 평가는 기술 간 전환과 장시간 실행 과정에서 안전 요구 사항(Safety Requirement)이 지속적으로 충족되는지 검증해야 한다.

시뮬레이션(Simulation)은 점진적으로 복잡해지는 임무를 구성하고 통합 실패(Integration Failure)를 식별하는 실용적인 환경을 제공한다. 제어된 시나리오(Controlled Scenario)는 특정 의존성을 분리하여 분석할 수 있으며, 무작위화된 환경(Randomized Environment)은 기술 전환(Skill Transition)과 작업 계획(Task Planning)의 약점을 드러낸다. 그러나 접촉 역학(Contact Dynamics), 센싱 한계(Sensing Limitation), 인간 활동(Human Activity), 하드웨어 변동성(Hardware Variability)이 성공적으로 보였던 기술 조합의 행동을 변화시킬 수 있으므로 실제 환경 시험(Real-World Testing)이 필요하다.

재현 가능한 임무 평가(Reproducible Mission Evaluation)를 위해서는 목표(Objective), 초기 조건(Initial Condition), 사용 가능한 자원(Available Resource), 허용된 행동(Permitted Action), 완료 기준(Completion Criteria)을 표준화하여 정의해야 한다. 평가자는 상위 수준 의사결정(High-Level Decision)과 개별 기술 결과(Individual Skill Outcome)를 연결하는 실행 기록(Execution Trace)을 보존해야 한다. 이를 통해 연구자는 임무 실패가 인식 오류(Perception Error), 잘못된 작업 분해(Incorrect Decomposition), 부적절한 순서 결정(Inappropriate Sequencing), 제어 한계(Control Limitation), 불충분한 복구 역량(Insufficient Recovery Capability) 중 무엇에서 비롯되었는지 식별할 수 있다.

궁극적으로 원자적 기술(Atomic Skills)에서 완전한 임무(Complete Missions)로의 발전은 개별 로봇 능력(Isolated Robotic Ability)을 입증하는 단계에서 통합된 물리적 자율성(Integrated Physical Autonomy)을 검증하는 단계로의 전환을 의미한다. 유능한 피지컬 인공지능(Physical AI) 시스템은 임무 진행 상황(Mission Progress)에 대한 일관된 이해를 유지하면서 기술을 선택하고, 조정하고, 모니터링하고, 적응시켜야 한다. 이러한 통합을 평가함으로써 개별 역량이 복잡한 실제 환경에서 신뢰할 수 있고, 안전하며, 일반화 가능한 운영(Reliable, Safe, and Generalizable Operation)을 지원할 수 있는지 확인할 수 있다.

## 06.03. Task Decomposition and Subgoal Evaluation

![](images/image3.png){width="7.268055555555556in" height="7.268055555555556in"}

작업 분해(Task Decomposition)는 복잡한 임무(Complex Mission)를 체계적으로 계획하고 실행하며 평가할 수 있는 더 작고 관리 가능한 하위 작업(Subtask)으로 변환하는 과정이다. 피지컬 인공지능(Physical AI)에서 이 과정은 상위 수준 목표(High-Level Objective)와 이를 달성하는 데 필요한 물리적 행동(Physical Action)을 연결한다. 로봇은 필요한 중간 목표(Intermediate Goal)를 식별하고, 목표 간 의존성(Dependency)을 파악하며, 환경 제약 조건(Environmental Constraint)과 가용 역량(Available Capability)을 고려하여 실행 가능한 순서로 구성해야 한다.

하위 목표 평가(Subgoal Evaluation)는 이러한 중간 목표가 전체 임무의 성공적인 완료에 실질적으로 기여하는지 검토한다. 로봇이 개별 하위 작업을 정확하게 수행하더라도 작업이 불완전하거나 순서가 잘못되거나 조정이 부적절하면 전체 목표 달성에 실패할 수 있다. 따라서 평가는 개별 하위 목표의 품질뿐 아니라 하위 목표들이 의도한 임무 결과에 집합적으로 기여하는 정도도 평가해야 한다.

효과적인 작업 분해는 명확하게 정의된 임무 목표에서 시작하며, 목표 달성에 필요한 조건을 식별한다. 예를 들어, 소포를 배송하도록 지시받은 이동형 매니퓰레이터(Mobile Manipulator)는 소포의 위치를 파악하고, 해당 위치로 이동하고, 소포를 안정적으로 파지하고, 목적지까지 운반하고, 소포를 내려놓은 다음 배송을 확인해야 할 수 있다. 각 하위 목표는 다음 실행 단계를 지원하는 측정 가능한 중간 조건(Measurable Intermediate Condition)을 설정한다.

작업 분해의 품질은 하위 작업이 충분히 구체적이고 실행 가능하며 검증 가능한지에 따라 달라진다. 물체를 준비한다는 모호한 하위 목표는 신뢰할 수 있는 실행이나 평가에 필요한 정보를 충분히 제공하지 못할 수 있다. 보다 정밀한 정의는 예상되는 물체 상태(Object State), 필요한 위치(Location), 승인 조건(Acceptance Condition)을 명시한다. 명확하게 정의된 하위 목표는 성공적인 진행과 불완전한 실행 또는 의도하지 않은 환경 변화(Environmental Change)를 구분하기 쉽게 한다.

하위 작업 간 의존성(Dependency)은 작업 분해의 품질을 결정하는 핵심 요소이다. 일부 작업은 이전 단계가 성공적으로 완료되어야 수행할 수 있지만, 다른 작업은 독립적으로 또는 병렬로 수행할 수 있다. 로봇은 물체를 안전하게 고정하기 전에 운반할 수 없지만, 다른 독립적인 준비 작업을 수행하는 동안 목적지를 검사할 수는 있다. 평가는 작업 분해가 이러한 의존성을 정확하게 반영하고 실현 가능한 실행 순서(Feasible Execution Order)를 생성하는지 확인해야 한다.

하위 목표의 경계(Subgoal Boundary)는 물리적 시스템의 역량과 한계도 반영해야 한다. 로봇의 기계적 도달 범위를 넘어서는 정밀 조작이나 지원되지 않는 조건에서도 신뢰할 수 있는 인식을 가정하는 작업 분해는 논리적으로 일관되더라도 실제 운영에서는 실행 불가능할 수 있다. 효과적인 평가는 각 하위 작업이 가용 센서(Sensor), 액추에이터(Actuator), 컴퓨팅 자원(Computational Resource), 제어 정책(Control Policy)을 사용하여 실행 가능한지 고려한다.

적절한 작업 분해 수준(Level of Decomposition)은 임무의 복잡성에 따라 달라진다. 지나치게 포괄적인 하위 작업은 중요한 의사결정을 감추고 실패 원인을 진단하기 어렵게 만든다. 반대로 지나치게 세분화된 하위 작업은 불필요한 계획 부담(Planning Overhead)을 유발하고 시스템이 유용한 행동 조합을 활용하지 못하게 할 수 있다. 평가는 신뢰할 수 있는 실행에 충분한 세부 정보를 제공하면서도 피할 수 있는 복잡성을 만들지 않는지 검토해야 한다.

계층적 분해(Hierarchical Decomposition)를 사용하면 로봇은 여러 추상화 수준(Level of Abstraction)에서 임무를 표현할 수 있다. 상위 수준 목표는 운영 단계(Operational Stage)로 나뉘고, 각 단계는 실행 가능한 행동(Executable Action)과 하위 수준 제어 명령(Low-Level Control Command)으로 더 세분화될 수 있다. 각 계층은 상위 계층의 의도를 유지하면서 하위 계층이 실행하는 데 필요한 충분한 세부 정보를 제공해야 한다. 평가는 이러한 계층 구조 전반에서 정보와 제약 조건이 일관되게 유지되는지 확인한다.

하위 목표 완료(Subgoal Completion)는 행동 명령을 내렸다는 사실만으로 의도한 결과가 달성되었다고 가정하지 않고 명시적으로 검증해야 한다. 부품을 배치하라는 지시를 받은 로봇이 이동 동작을 완료했더라도 부품을 잘못된 위치에 놓을 수 있다. 평가는 관측된 물리적 상태(Physical State)를 지정된 완료 조건(Completion Condition)과 비교해야 한다. 이러한 구분은 시스템이 시도한 행동을 성공적인 결과로 간주하는 것을 방지하고 불완전하거나 잘못된 실행을 감지할 수 있도록 한다.

진행 상황 평가(Progress Evaluation)는 부분적인 완료(Partial Completion)도 고려해야 한다. 하위 작업이 일부 필수 조건을 충족하더라도 다른 조건은 만족하지 못할 수 있다. 예를 들어, 로봇이 배송 장소에 도착했지만 배치를 위해 필요한 방향으로 소포를 정렬하지 못할 수 있다. 중간 진행 상황을 기록하면 단순한 성공 또는 실패의 이진 레이블(Binary Label)만 부여하는 것보다 더 많은 진단 정보를 얻을 수 있다. 그러나 부분 점수(Partial Credit)가 임무 완료나 안전에 필수적인 요구 사항의 미충족을 가려서는 안 된다.

하위 목표의 성공과 전체 임무의 성공 사이의 관계가 항상 단순한 것은 아니다. 일부 하위 작업은 필수적이지만 다른 작업은 효율성을 향상시키거나 동일한 목표에 도달하기 위한 대체 경로를 제공한다. 선택적인 행동이 실패하더라도 최종 결과에 미치는 영향은 작을 수 있지만, 핵심 선행 조건(Critical Prerequisite)에서 발생한 작은 오류는 전체 임무를 무효화할 수 있다. 평가는 핵심 의존성과 유연한 대안을 구분하고 운영상 중요성에 따라 결과에 가중치를 부여해야 한다.

환경 조건(Environmental Condition)이 변할 때 작업 분해는 적응성을 유지해야 한다. 예상하지 못한 장애물, 사용할 수 없는 물체, 파지 실패는 원래 계획을 무효화할 수 있다. 유능한 시스템은 어떤 하위 목표를 여전히 달성할 수 있는지 식별하고, 변경된 의존성을 파악하며, 적절한 대안을 생성해야 한다. 평가는 재계획(Replanning)이 이미 완료된 작업을 불필요하게 반복하지 않으면서 전체 목표를 유지하는지 측정해야 한다.

복구 행동(Recovery Behavior) 역시 작업 분해의 품질에 영향을 받는다. 하위 목표가 실패하면 시스템은 영향을 받은 단계를 식별하고 해당 실패를 국소적으로 수정할 수 있는지, 아니면 이전 결정까지 재검토해야 하는지 판단해야 한다. 파지 실패는 접근 방식을 바꾸는 것으로 해결할 수 있지만, 물체를 사용할 수 없다는 사실이 확인되면 다른 공급 위치를 선택해야 할 수 있다. 평가는 시스템이 이전 행동을 단순히 반복하는 대신 실제 원인을 해결하는 복구 결정을 내리는지 검토해야 한다.

장기 임무(Long-Horizon Mission)에서는 시간이 흐르면서 이전 하위 목표의 유효성이 달라질 수 있기 때문에 추가적인 문제가 발생한다. 이전에 접근할 수 있었던 위치가 막힐 수 있으며, 성공적으로 식별한 물체가 회수 전에 이동할 수도 있다. 시스템은 완료된 행동과 여전히 유효한 조건을 구분해야 한다. 따라서 하위 목표 평가는 과거의 완료 여부뿐 아니라 관련 세계 상태(World State)가 현재도 유효한지 고려해야 한다.

시간적 제약 조건(Temporal Constraint)은 작업 분해를 평가하는 또 다른 차원이다. 일부 하위 작업은 마감 시간(Deadline) 전에 완료되어야 하며, 다른 작업은 특정 시간 범위(Time Window) 안에서 수행되거나 외부 사건과 동기화되어야 한다. 이러한 시간 요구 사항을 무시하면 논리적으로 올바른 작업 분해도 실제 운영에서는 실패할 수 있다. 평가는 계획이 실행 시간, 자원 가용성(Resource Availability), 동기화(Synchronization), 지연의 결과를 고려하는지 검토해야 한다.

자원 제약 조건(Resource Constraint)도 하위 목표의 선택과 실행 순서에 영향을 미친다. 배터리 용량(Battery Capacity), 적재 한도(Payload Limit), 가용 도구(Available Tool), 컴퓨팅 부하(Computational Load), 공동 작업 공간의 사용 가능 여부는 계획된 작업 순서의 실현 가능성을 결정할 수 있다. 로봇은 작업을 계속하기 전에 충전하거나 장비를 회수하거나 제한된 구역을 확보해야 할 수 있다. 평가는 자원 요구 사항이 정확하게 표현되고 선택된 작업 분해가 지속적인 임무 수행(Sustained Mission Execution)을 지원하는지 확인해야 한다.

안전 요구 사항(Safety Requirement)은 작업 분해와 하위 목표 평가 모두에 통합되어야 한다. 각 단계에서 개별적으로 허용 가능한 행동도 단계 간 상호작용을 고려하지 않으면 전체적으로 안전하지 않은 결과를 초래할 수 있다. 예를 들어, 물체를 이동하는 과정에서 이후 임무에 필요한 비상 통로(Emergency Route)가 막힐 수 있다. 평가는 하위 목표 간 전환 과정에서도 안전 제약 조건이 유지되는지, 위험하거나 되돌릴 수 없는 행동(Hazardous or Irreversible Action) 전에 적절한 확인 절차가 포함되어 있는지 검증해야 한다.

하위 목표 평가는 계획과 추론(Planning and Reasoning)의 약점을 발견하는 데도 도움이 된다. 시스템이 불필요한 단계를 반복적으로 생성하거나 필요한 선행 조건을 놓치거나 임무 진행에 기여하지 않는 행동을 선택한다면 문제는 하위 수준 제어기(Low-Level Controller)가 아니라 작업 분해 전략(Decomposition Strategy)에 있을 수 있다. 하위 목표 정의, 의존성 관계, 실행 결과, 복구 결정을 기록하면 연구자는 이러한 문제를 구분하고 적절한 시스템 구성 요소를 개선할 수 있다.

신뢰할 수 있는 평가를 위해서는 일관된 작업 명세(Task Specification)와 반복 가능한 평가 조건(Repeatable Evaluation Condition)이 필요하다. 벤치마크는 임무 목표, 하위 목표의 승인 기준, 의존성 규칙, 자원 한계, 종료 조건을 정의해야 한다. 다양한 환경에서 반복 시험을 수행하면 작업 분해 전략이 견고한지 또는 익숙한 시나리오에 의존하는지 확인할 수 있다. 임무 완료율과 함께 하위 목표 정확도, 실행 시간, 복구 빈도, 개입 요구 사항을 보고하면 시스템 성능을 더욱 종합적으로 파악할 수 있다.

궁극적으로 작업 분해(Task Decomposition)와 하위 목표 평가(Subgoal Evaluation)는 상위 수준 임무 추론(High-Level Mission Reasoning)과 측정 가능한 물리적 결과(Measurable Physical Outcome)를 연결한다. 효과적인 시스템은 복잡한 목표를 실행 가능한 중간 목표로 분해하고, 의존성을 유지하며, 진행 상황을 검증하고, 가정이 무효화될 때 적응해야 한다. 이러한 역량을 평가하면 피지컬 인공지능(Physical AI) 시스템이 개별적으로 성공한 기술의 집합을 수행하는 데 그치지 않고 일관되고 신뢰할 수 있으며 안전한 임무 실행(Coherent, Reliable, and Safe Mission Execution)을 구성할 수 있는지 확인할 수 있다.

## 06.04. Temporal Credit and Progress Metrics

![](images/image4.png){width="7.268055555555556in" height="7.268055555555556in"}

시간적 기여도 할당(Temporal Credit Assignment)은 서로 다른 시점에 이루어진 행동과 의사결정이 작업의 최종 결과에 어떻게 기여하는지 판단하는 과정이다. 피지컬 인공지능(Physical AI)에서는 행동의 결과가 훨씬 나중에 나타날 수 있기 때문에 장기 임무(Long-Horizon Mission)에서 이 문제가 특히 중요해진다. 평가는 이전의 어떤 결정이 진행 상황을 개선하고, 위험을 발생시키거나, 후속 작업에서 드러난 실패의 원인이 되었는지 식별해야 한다.

진행 상황 지표(Progress Metrics)는 로봇이 의도한 목표를 향해 얼마나 효과적으로 나아가는지 측정함으로써 시간적 기여도 할당을 보완한다. 전통적인 성공 지표(Success Metrics)는 전체 임무를 성공 또는 실패로 분류하는 경우가 많아 중간 성능(Intermediate Performance)에 대한 정보가 제한적이다. 반면 진행 상황 중심 평가(Progress-Oriented Evaluation)는 작업 상태(Task State)의 의미 있는 변화, 완료된 하위 목표(Subgoal), 남아 있는 요구 사항(Remaining Requirements), 실행 과정 전반에서의 진행 품질을 검토한다.

장기 작업(Long-Horizon Task)에는 행동과 결과 사이에 지연된 의존성(Delayed Dependency)이 존재하는 경우가 많다. 로봇이 초기 조작 단계에서 물체를 잘못 배치하더라도 실제 실패는 다른 부품을 조립해야 하는 시점에 발생할 수 있다. 최종적으로 실패한 행동에만 책임을 부여하면 근본적인 원인(Underlying Cause)을 잘못 해석하게 된다. 시간적 평가(Temporal Evaluation)는 이후의 결과를 관련된 이전 의사결정 및 환경 변화와 연결해야 한다.

근본적인 과제 중 하나는 생산적인 행동(Productive Action)과 단순히 시간이나 자원을 소비하는 활동을 구분하는 것이다. 로봇은 임무 목표에 가까워지지 않으면서도 반복적으로 이동하거나 물체를 조작하거나 유효한 명령을 실행할 수 있다. 따라서 진행 상황 지표는 수행된 행동의 개수가 아니라 목표와 관련된 조건(Goal-Relevant Condition)의 검증된 변화를 반영해야 한다. 이러한 구분은 과도한 활동을 의미 있는 작업 진전으로 잘못 해석하는 것을 방지한다.

하위 목표 완료(Subgoal Completion)는 진행 상황을 측정하기 위한 실용적인 기반을 제공한다. 복잡한 임무는 명시적인 승인 조건(Acceptance Condition)을 갖는 중간 목표(Intermediate Objective)로 분해할 수 있다. 평가자는 달성된 하위 목표, 완료되지 않은 하위 목표, 환경 변화로 인해 무효화된 하위 목표를 기록할 수 있다. 그러나 하위 목표의 난이도, 중요성, 의존성 관계(Dependency Relationship)가 크게 다를 경우 완료된 하위 목표의 개수만 계산하는 것은 오해를 유발할 수 있다.

가중 진행 상황 지표(Weighted Progress Metrics)는 중요하거나 많은 자원이 필요한 목표에 더 높은 중요도를 부여하여 이러한 차이를 반영한다. 예를 들어, 위험 물체(Hazardous Object)를 안전하게 고정하는 작업은 여러 개의 일상적인 내비게이션 동작보다 임무 준비 상태(Mission Readiness)에 더 크게 기여할 수 있다. 가중치 체계(Weighting Scheme)는 평가 전에 정의하고 임무 요구 사항에 근거하여 정당화해야 한다. 그렇지 않으면 임의의 가중치가 비교 결과를 왜곡하거나 실제 임무 성과를 개선하지 않는 행동에 보상을 부여할 수 있다.

시간적 기여도 할당은 직접적인 영향(Direct Effect)과 간접적인 결과(Indirect Consequence)를 구분해야 한다. 내비게이션 결정은 조작 품질(Manipulation Quality)에 즉각적인 영향을 주지 않을 수 있지만, 로봇의 접근 방향(Approach Orientation)과 사용 가능한 작업 공간(Workspace)을 결정할 수 있다. 마찬가지로 초기 인식 오류(Perception Error)는 이후 여러 계획 결정에 영향을 미칠 수 있다. 평가는 시간적으로 가까운 사건 사이에 반드시 인과관계가 있다고 가정하지 않으면서 가능한 인과관계(Causal Relationship)를 식별할 수 있도록 충분한 실행 이력(Execution History)을 보존해야 한다.

궤적 기반 평가(Trajectory-Based Evaluation)는 이러한 관계를 체계적으로 분석하는 방법을 제공한다. 궤적(Trajectory)은 관측(Observation), 추정 상태(Estimated State), 선택된 행동(Selected Action), 중간 결과(Intermediate Outcome), 관련 환경 상태 전이(Environmental Transition)를 기록한다. 평가자는 이러한 시퀀스를 분석하여 진행 속도가 빨라지거나, 정체되거나, 후퇴하거나, 안전하지 않게 된 시점을 파악할 수 있다. 이러한 분석은 계획 실패(Planning Failure), 제어 한계(Control Limitation), 잘못된 가정(Incorrect Assumption), 지연된 오류 전파(Delayed Error Propagation)의 진단을 지원한다.

물리적 작업 실행(Physical Task Execution)에서 진행 상황이 반드시 단조롭게 증가(Monotonic Increase)하는 것은 아니다. 로봇은 장애물을 피하기 위해 일시적으로 목적지에서 멀어지거나, 접근성을 높이기 위해 물체를 재배치하거나, 조립을 완료하기 전에 이전 행동을 되돌릴 수 있다. 이러한 행동은 목표까지의 즉각적인 거리가 증가하더라도 합리적인 진행(Rational Progress)을 의미할 수 있다. 평가는 미래의 성공을 지원하는 일시적인 후퇴(Temporary Regression)와 불필요하거나 비효율적인 우회(Unnecessary or Ineffective Detour)를 구분해야 한다.

잠재 함수 기반 진행 측정(Potential-Based Progress Measure)은 목표 상태(Goal State)까지의 추정 거리 변화로 진행 상황을 표현할 수 있다. 이 거리는 기하학적(Geometric), 기호적(Symbolic) 또는 작업별 상태 변수(Task-Specific State Variable)를 기반으로 정의할 수 있다. 그러나 성공적인 실행에 중간 준비 작업(Intermediate Preparation)이나 비국소적 행동(Nonlocal Action)이 필요한 경우 단순한 거리 측정은 실패할 수 있다. 따라서 진행 함수(Progress Function)는 관련 작업 구조(Task Structure)를 반영하고 운영 제약 조건(Operational Constraint)을 위반하는 지름길에 보상을 부여하지 않도록 설계해야 한다.

시간적 효율성(Temporal Efficiency)은 또 다른 중요한 평가 차원이다. 두 로봇이 동일한 중간 상태(Intermediate State)에 도달하더라도 필요한 시간, 에너지, 연산량(Computation)은 다를 수 있다. 자원 소비 단위당 진행 상황(Progress per Unit of Resource Consumption)을 측정하면 운영 효율성(Operational Efficiency)을 파악할 수 있지만, 빠른 진행이 항상 바람직한 것은 아니다. 안전 여유(Safety Margin), 불확실성 감소(Uncertainty Reduction), 후속 단계 준비는 즉각적인 진행이 제한적이더라도 추가적인 노력을 정당화할 수 있다.

지연 보상(Delayed Reward)은 학습(Learning)과 평가(Evaluation) 모두에서 어려움을 발생시킨다. 성공적인 최종 결과는 개별 기여도를 분리하기 어려운 수많은 이전 결정에 의존할 수 있다. 보상 분해(Reward Decomposition), 반사실적 분석(Counterfactual Analysis), 중간 이정표 기여도 할당(Intermediate Milestone Attribution)과 같은 기법은 유용한 진단 정보를 제공할 수 있다. 그러나 이러한 방법은 작업 동역학(Task Dynamics)에 대한 가정에 의존하므로 뒷받침하는 증거 없이 확정적인 인과적 설명(Causal Explanation)으로 간주해서는 안 된다.

반사실적 평가(Counterfactual Evaluation)는 이전에 다른 결정을 내렸다면 더 나은 결과가 나타났을 가능성이 있는지 검토한다. 시뮬레이션(Simulation)에서는 평가자가 이전 상태를 복원하고 제어된 조건에서 대체 행동(Alternative Action)을 비교할 수 있다. 이러한 접근 방식은 영향력이 큰 결정을 식별하고 관련 없는 사건에 실패의 원인을 잘못 부여하는 것을 방지하는 데 도움이 된다. 실제 물리적 환경에서는 정확한 상태 복원(State Restoration)이 어려운 경우가 많으므로 반복 시험(Repeated Trial), 근사적 조건 일치(Approximate Matching), 모델 기반 분석(Model-Based Analysis)이 필요하다.

시간적 기여도를 할당할 때는 불확실성(Uncertainty)을 고려해야 한다. 센서 잡음(Sensor Noise), 부분 관측 가능성(Partial Observability), 확률적 접촉 동역학(Stochastic Contact Dynamics), 변화하는 환경은 의사결정과 결과 사이의 관계를 불명확하게 만들 수 있다. 로봇이 합리적인 행동을 선택했더라도 예측할 수 없는 외란(Unpredictable Disturbance)으로 인해 실패할 수 있다. 평가는 충분한 증거가 있는 경우 의사결정 품질(Decision Quality)과 실제 발생한 결과(Realized Outcome)를 구분하고, 인과적 책임(Causal Responsibility)을 확립할 수 없는 경우에는 불확실성을 보고해야 한다.

진행 상황 지표는 복구 행동(Recovery Behavior)도 인식해야 한다. 파지 또는 내비게이션 시도가 실패한 후 로봇은 임무를 재개하기 전에 사용 가능한 상태(Usable State)를 복원하는 데 시간을 소비할 수 있다. 즉각적인 목표 근접성(Goal Proximity)만을 기준으로 하는 지표는 이러한 필수 복구 과정을 불리하게 평가할 수 있다. 보다 유용한 평가는 손실된 진행 상황(Lost Progress), 복구 시간(Recovery Duration), 복원된 역량(Restored Capability), 후속 작업 완료(Subsequent Task Completion)를 기록하여 수정 행동(Corrective Action)이 효과적이었는지 판단한다.

임무 진행 상황(Mission Progress)은 여러 시간적 규모(Temporal Scale)에서 표현할 수 있다. 단기 지표(Short-Term Metrics)는 즉각적인 실행 품질(Execution Quality)을 측정하고, 중기 지표(Medium-Term Metrics)는 하위 목표 달성(Subgoal Achievement)을 측정하며, 장기 지표(Long-Term Metrics)는 임무 완료(Mission Completion)와 지속적인 자율성(Sustained Autonomy)을 평가한다. 이러한 측정값은 지역적 개선(Local Improvement)이 전체적인 실패(Global Failure)를 감추지 않도록 서로 연결되어야 한다. 개별 움직임을 최적화하면서 전체 임무 목표를 반복적으로 포기하는 시스템은 높은 종합 평가를 받아서는 안 된다.

안전성(Safety)과 진행 상황(Progress)은 함께 평가해야 한다. 허용할 수 없는 위험(Unacceptable Risk)을 감수하여 달성한 목표 진전은 바람직하지 않기 때문이다. 로봇은 제한 구역(Restricted Area)에 진입하여 경로를 단축하거나 안전한 운영 한계(Safe Operating Limit)를 초과하여 조작 속도를 높일 수 있다. 진행 상황 지표는 실현 가능성(Feasibility)과 안전 제약 조건(Safety Constraint)을 반영해야 하며, 안전에 중대한 위반(Safety-Critical Violation)은 통합 성능 점수(Aggregated Performance Score)에 숨기지 않고 별도로 보고해야 한다.

인간 개입(Human Intervention)은 외부에서 제공된 수정 조치가 후속 하위 목표의 성공을 결정할 수 있기 때문에 시간적 기여도 분석을 복잡하게 만든다. 운영자가 위치 추정 실패(Localization Failure)를 해결했다면 이후의 자율 내비게이션(Autonomous Navigation)을 로봇이 독립적으로 복구했다는 증거로 해석해서는 안 된다. 평가 기록(Evaluation Record)은 개입 시점(Intervention Timing), 지원 유형(Assistance Type), 영향을 받은 작업 단계(Affected Task Stage)를 식별해야 한다. 이를 통해 자율적으로 달성한 진행 상황과 외부 지원으로 가능해진 진행 상황을 구분할 수 있다.

벤치마크 설계(Benchmark Design)에서는 시험 전에 진행 상황의 정의(Progress Definition), 시간적 샘플링 절차(Temporal Sampling Procedure), 하위 목표 가중치(Subgoal Weight), 기여도 할당 가정(Credit Assignment Assumption)을 명시해야 한다. 평가 로그(Evaluation Log)는 타임스탬프(Timestamp), 행동 이력(Action History), 상태 추정(State Estimate), 검증 결과(Verification Result), 개입 기록(Intervention Record)을 보존해야 한다. 다양한 조건에서 반복 시험을 수행하면 관측된 진행 패턴(Progress Pattern)이 일관적인지 또는 유리한 환경에 의존하는지 확인할 수 있다. 통계 보고(Statistical Reporting)에는 변동성(Variability)과 불확실성이 포함되어야 한다.

견고한 평가 프레임워크(Robust Evaluation Framework)는 최종 임무 성공(Final Mission Success), 중간 진행 상황(Intermediate Progress), 시간적 효율성(Temporal Efficiency), 복구 품질(Recovery Quality), 인과적 진단(Causal Diagnostics)을 결합해야 한다. 단일 지표(Single Metric)만으로는 장기간의 물리적 상호작용(Extended Physical Interaction)이 갖는 복잡성을 완전히 표현할 수 없다. 다차원 평가(Multi-Dimensional Assessment)는 신뢰할 수 있는 진행을 달성하는 시스템과 일시적인 성공, 비효율적인 반복, 변화하는 조건에서 취약한 실행 전략(Fragile Execution Strategy)을 보이는 시스템을 구분하는 데 도움이 된다.

궁극적으로 시간적 기여도 할당(Temporal Credit Assignment)과 진행 상황 지표(Progress Metrics)는 피지컬 인공지능(Physical AI) 시스템이 임무를 완료했는지뿐 아니라 시간에 따른 의사결정이 성공 또는 실패에 어떻게 기여했는지도 설명한다. 이들은 지역적 행동(Local Action)을 지연된 결과(Delayed Consequence)와 연결하고, 숨겨진 의존성(Hidden Dependency)을 드러내며, 계획과 제어의 체계적인 개선(Systematic Improvement)을 지원한다. 이러한 요소의 통합은 복잡한 물리적 환경에서 신뢰할 수 있는 장기 자율성(Dependable Long-Horizon Autonomy)을 평가하는 데 필수적이다.

## 06.05. Long Horizon Task Success

![](images/image5.png){width="7.268055555555556in" height="7.268055555555556in"}

장기 작업 성공(Long-Horizon Task Success)은 피지컬 인공지능(Physical AI) 시스템이 장시간에 걸친 일련의 조정된 행동과 의사결정을 통해 완전한 임무 목표(Complete Mission Objective)를 달성하는 능력을 의미한다. 개별 기술이나 즉각적인 결과에 초점을 맞추는 단기 평가(Short-Horizon Evaluation)와 달리, 장기 작업 성공은 여러 단계에 걸쳐 지속적인 역량(Sustained Competence)을 요구한다. 시스템은 실행 과정 전반에서 목표의 일관성(Goal Consistency)을 유지하고, 의존성(Dependency)을 관리하며, 변화에 적절하게 대응해야 한다.

장기 작업의 성공을 정의하려면 최종 행동이 완료되었는지 관찰하는 것 이상의 평가가 필요하다. 로봇은 계획된 모든 움직임을 실행하더라도 의도한 물리적 결과(Physical Outcome)를 달성하지 못할 수 있다. 예를 들어, 배송 로봇(Delivery Robot)이 목적지에 도착했지만 올바른 소포를 전달하지 못할 수 있다. 따라서 평가는 단순한 행동 완료(Action Completion)가 아니라 검증된 환경 상태(Verified Environmental State)를 기반으로 명시적인 임무 승인 기준(Mission Acceptance Criteria)을 수립해야 한다.

완전한 임무(Complete Mission)는 일반적으로 서로 다른 운영 요구 사항(Operational Requirement)을 가진 상호 연결된 하위 작업(Subtask)으로 구성된다. 이동형 매니퓰레이터(Mobile Manipulator)는 물체를 식별하고, 해당 물체로 이동하고, 파지하고, 운반하고, 정확하게 배치한 다음 최종 배치 상태를 확인해야 할 수 있다. 성공은 전체 시퀀스(Sequence)에 걸쳐 필수 조건을 충족하는 데 달려 있다. 핵심 선행 조건(Critical Prerequisite)에서 실패하면 이후의 행동이 올바르게 실행되더라도 그 결과가 무효화될 수 있다.

장기 작업 성공 지표(Long-Horizon Success Metrics)는 임무 완료(Mission Completion)와 부분적인 진행 상황(Partial Progress)을 구분해야 한다. 대부분의 하위 작업을 완료했지만 마지막 단계에서 실패한 로봇은 시작 직후 실패한 로봇과 서로 다른 역량을 보여준다. 이진 성공 지표(Binary Success Indicator)는 최종 달성 여부를 명확하게 측정하지만 실행 품질(Execution Quality)의 중요한 차이를 감춘다. 보완적인 진행 상황 지표(Progress Metrics)는 부분적인 완료를 전체 성공으로 간주하지 않으면서 미완료 임무의 특성을 설명하는 데 도움이 된다.

임무 성공은 중간 상태(Intermediate State)의 유효성도 고려해야 한다. 로봇이 일시적으로 하위 목표(Subgoal)를 충족했더라도 임무가 끝나기 전에 해당 상태가 무효화될 수 있다. 예를 들어, 준비 단계에서 물체를 올바르게 배치했지만 이후 조작 과정에서 위치가 변경될 수 있다. 평가는 관련 의존성이 실제로 작용하는 시점에도 필수 조건이 유지되는지, 그리고 최종 세계 상태(Final World State)가 모든 필수 요구 사항(Mandatory Requirement)을 충족하는지 확인해야 한다.

필수 작업의 수가 증가하면 긴 시퀀스를 완료할 확률이 감소할 수 있다. 개별 행동이 서로 독립적이고 동일한 성공 확률(Success Probability)을 갖는다는 단순화된 가정에서는 전체 무중단 성공 확률(Uninterrupted Success Probability)이 개별 확률의 곱으로 계산된다. 각각 0.98의 성공 확률을 갖는 20개 행동의 전체 성공 확률은 약 0.668이다. 실제 시스템에서는 오류 간 상관관계(Correlated Error)가 존재하고 복구(Recovery)를 통해 진행 상황을 회복할 수 있으므로 더욱 상세한 분석이 필요하다.

복구 역량(Recovery Capability)은 실질적인 임무 성공을 결정하는 핵심 요소이다. 로봇은 파지 실패(Grasp Failure), 일시적인 위치 추정 오류(Localization Error), 차단된 경로(Blocked Route)를 경험하더라도 목표를 완료할 능력을 영구적으로 잃지 않을 수 있다. 평가는 무중단 성공(Uninterrupted Success), 복구 후 성공(Recovered Success), 최종 실패(Terminal Failure)를 구분해야 한다. 이러한 구분은 시스템이 이상적인 조건에서만 성공하는 것이 아니라 외란(Disturbance)이 발생하더라도 임무의 연속성(Mission Continuity)을 유지할 수 있는지 보여준다.

그러나 성공적인 복구가 실패로 인한 운영 비용(Operational Cost)을 없애는 것은 아니다. 반복적인 시도는 임무 수행 시간(Mission Duration), 에너지 소비(Energy Consumption), 기계적 마모(Mechanical Wear), 위험 노출(Hazard Exposure)을 증가시킬 수 있다. 여러 차례의 수정 행동(Corrective Action) 이후에야 임무를 완료하는 시스템은 최소한의 중단으로 일관되게 임무를 완료하는 시스템보다 실용성이 낮을 수 있다. 따라서 장기 작업 평가는 복구 빈도(Recovery Frequency), 복구 시간(Recovery Duration), 관련 자원 비용(Resource Cost)을 보고해야 한다.

자율 임무 성공(Autonomous Mission Success)은 지원을 받은 완료(Assisted Completion)와 구분해야 한다. 인간 운영자(Human Operator)는 예상하지 못한 장애물을 해결하고, 인식 오류(Perception Error)를 수정하고, 제어기(Controller)를 재설정하거나 추가 지시를 제공할 수 있다. 이러한 지원을 통해 최종적으로 임무 목표를 달성하더라도 외부 지원(External Assistance)은 결과의 의미를 변화시킨다. 평가 절차(Evaluation Protocol)는 허용되는 개입 수준(Intervention Level)을 명시하고 완전 자율 완료(Fully Autonomous Completion), 지원을 받은 완료, 실패 결과를 구분하여 보고해야 한다.

안전성(Safety)은 의미 있는 장기 작업 성공을 위한 필수 조건이다. 충돌(Collision)을 일으키거나 장비를 손상시키거나 제한 구역(Restricted Zone)을 위반하거나 사람을 허용할 수 없는 위험(Unacceptable Risk)에 노출시키면서 작업을 완료한 결과는 안전한 완료(Safe Completion)와 동등하게 평가할 수 없다. 평가는 필수 안전 제약 조건(Mandatory Safety Constraint)을 정의하고 생산성 지표(Productivity Metrics)와 독립적으로 위반 사항을 기록해야 한다. 중대한 안전 실패(Critical Safety Failure)는 최종 목표가 물리적으로 달성되었더라도 임무 성공을 무효화할 수 있다.

실행 품질(Execution Quality)은 이진 완료 여부를 넘어서는 또 다른 평가 차원이다. 두 로봇이 동일한 목표를 달성하더라도 정밀도(Precision), 안정성(Stability), 부드러운 동작(Smoothness), 환경 교란(Environmental Disturbance)의 수준은 다를 수 있다. 조작 작업(Manipulation Task)은 지정된 허용 오차(Tolerance) 내의 배치 정확도를 요구할 수 있으며, 내비게이션 임무(Navigation Mission)는 이격 거리(Clearance)와 위치 정확도(Positioning Accuracy)에 대한 요구 사항을 가질 수 있다. 성공 기준(Success Criteria)은 의도한 응용 분야에 필요한 품질을 반영해야 한다.

시간적 요구 사항(Temporal Requirement)도 임무 성공의 해석에 영향을 미친다. 로봇이 모든 하위 작업을 최종적으로 완료하더라도 중요한 마감 시간(Deadline)을 놓치거나 다른 시스템과 동기화(Synchronization)하지 못할 수 있다. 물류(Logistics), 제조(Manufacturing), 검사(Inspection) 응용 분야에서는 완료 지연(Delayed Completion)이 운영 가치를 감소시키거나 없앨 수 있다. 평가는 요구된 시간 제약 조건(Time Constraint) 내의 완료와 지연된 완료를 구분하고 시간 요구 사항 위반(Timing Violation)의 결과를 보고해야 한다.

자원 효율성(Resource Efficiency)은 성공적인 실행과 함께 고려해야 한다. 장기 임무는 에너지(Energy), 연산 자원(Computation), 통신 대역폭(Communication Bandwidth), 기계적 자원(Mechanical Resource)을 소비한다. 필수 자원을 모두 소진하면서 임무를 완료한 로봇은 이후 안전하게 운영을 지속하지 못할 수 있다. 평가는 특히 단발성 시연(Isolated Demonstration)이 아니라 지속적인 배포(Continuous Deployment)의 일부로 임무가 수행되는 경우 자원 소비량(Resource Consumption)과 남아 있는 운영 능력(Remaining Operational Capacity)을 측정해야 한다.

장기 작업 성공은 시간에 걸쳐 정확한 작업 표현(Task Representation)과 세계 표현(World Representation)을 유지하는 능력에 의존한다. 로봇은 완료된 작업을 기억하고, 관련 지시를 보존하고, 물체 상태(Object State)를 추적하며, 환경이 변할 때 가정(Assumption)을 갱신해야 한다. 기억(Memory)이나 상태 추정(State Estimation)의 오류는 중복 행동(Redundant Action), 요구 사항 누락(Missed Requirement), 잘못된 종료(Incorrect Termination)를 유발할 수 있다. 평가는 시스템이 임무 전반에서 일관된 의사결정을 지원하는 데 필요한 정보를 유지하는지 확인해야 한다.

계획 및 재계획 역량(Planning and Replanning Competence)도 임무 결과에 영향을 미친다. 성공적인 시스템은 예상하지 못한 조건에 적응하면서 여러 시간적 규모(Temporal Scale)에 걸친 행동을 조정해야 한다. 경로가 차단되거나 물체를 사용할 수 없게 되면 로봇은 원래 목표를 불필요하게 포기하지 않으면서 실행 가능한 대안(Feasible Alternative)을 식별해야 한다. 평가는 수정된 계획(Revised Plan)이 임무 제약 조건(Mission Constraint)을 유지하고 지속적인 진행(Continued Progress)을 지원하는지 판단해야 한다.

임무 성공은 고정된 실험실 조건(Fixed Laboratory Condition)뿐 아니라 환경 변동성(Environmental Variability) 속에서도 평가해야 한다. 조명(Lighting), 지형(Terrain), 물체 배치(Object Arrangement), 인간 활동(Human Activity), 센서 품질(Sensor Quality)의 변화는 장시간에 걸친 성능에 영향을 미칠 수 있다. 익숙한 환경에서 반복적으로 성공하는 시스템도 작은 환경 변화에서는 실패할 수 있다. 따라서 벤치마킹(Benchmarking)은 임무 완료의 견고성(Robustness)을 검토하기 위해 제어된 외란(Controlled Disturbance)과 처음 접하는 환경 구성(Unseen Configuration)을 포함해야 한다.

통계적 신뢰성(Statistical Reliability)은 소수의 성공적인 시연만으로는 신뢰할 수 있는 자율성(Dependable Autonomy)을 입증할 수 없기 때문에 특히 중요하다. 평가는 대표적인 조건(Representative Condition)에서 반복 시험(Repeated Trial)을 수행하고 적절한 불확실성 추정(Uncertainty Estimate)과 함께 완료율(Completion Rate)을 보고해야 한다. 실패 분포(Failure Distribution), 임무 수행 시간(Mission Duration), 개입 빈도(Intervention Frequency)는 추가적인 해석 정보를 제공한다. 시스템 간 비교에서는 작업 난이도(Task Difficulty)와 외란 노출(Disturbance Exposure)의 차이를 고려해야 한다.

장기 작업 성공은 임무 신뢰성(Mission Reliability)이 시간이나 작업 복잡도(Task Complexity)에 따라 어떻게 변화하는지 분석하는 생존 분석 기반 측정(Survival-Oriented Measurement)을 통해서도 평가할 수 있다. 최종 실패 없이 운영 상태를 유지할 확률은 실행이 지속될수록 감소할 수 있다. 생존 곡선(Survival Curve), 실패까지의 시간 분포(Time-to-Failure Distribution), 서로 다른 임무 길이(Mission Length)에서의 완료 확률(Completion Probability)은 종합 성공률(Aggregate Success Rate)만으로는 드러나지 않는 한계를 보여줄 수 있다.

연속 운영(Continuous Operation)은 단일 임무 완료와 반복적인 임무 수행 전반에서 신뢰할 수 있는 성능을 유지하는 능력을 구분하게 한다. 로봇은 한 번의 작업에서는 성공하더라도 위치 추정 드리프트(Localization Drift), 열 스트레스(Thermal Stress), 자원 고갈(Resource Depletion)이 점진적으로 누적될 수 있다. 평가는 시스템이 관련 작업 상태(Task State)를 초기화하고, 운영 준비 상태(Operational Readiness)를 회복하며, 과도한 유지보수(Maintenance)나 개입 없이 연속적인 임무(Successive Mission)를 완료할 수 있는지 확인해야 한다.

포괄적인 장기 작업 성공 프레임워크(Comprehensive Long-Horizon Success Framework)는 최종 목표 충족(Final Objective Satisfaction), 하위 목표 완료(Subgoal Completion), 안전 준수(Safety Compliance), 실행 품질(Execution Quality), 자율성 수준(Autonomy Level), 시간적 효율성(Temporal Efficiency), 자원 소비(Resource Consumption)를 결합해야 한다. 이러한 평가 차원은 단일 통합 점수(Aggregate Score)에 감춰지지 않고 각각 독립적으로 해석할 수 있어야 한다. 명확한 보고는 연구자가 실제로 신뢰할 수 있는 시스템과 유리한 조건이나 광범위한 지원을 통해 간헐적으로 성공하는 시스템을 구분할 수 있도록 한다.

궁극적으로 장기 작업 성공(Long-Horizon Task Success)은 개별 로봇 역량(Isolated Robotic Capability)을 입증하는 단계에서 지속적인 임무 수준 자율성(Sustained Mission-Level Autonomy)을 검증하는 단계로의 전환을 의미한다. 성공적인 피지컬 인공지능(Physical AI) 시스템은 안전성을 유지하고, 불확실성(Uncertainty)을 관리하고, 외란(Disturbance)으로부터 복구하며, 실질적인 제약 조건(Practical Constraint) 내에서 검증된 목표(Verified Objective)를 달성해야 한다. 이러한 특성을 종합적으로 평가함으로써 시스템이 복잡한 실제 환경에서 신뢰할 수 있고 반복 가능한 성능(Reliable and Repeatable Performance)을 제공할 수 있는지 확인할 수 있다.

## 06.06. Compounding Error and Error Propagation

![](images/image6.png){width="7.268055555555556in" height="7.268055555555556in"}

오류 누적(Compounding Error)은 장시간의 작업 실행 과정에서 연속적인 행동, 관측, 의사결정에 걸쳐 작은 부정확성이 축적되는 현상을 의미한다. 피지컬 인공지능(Physical AI)에서는 사소한 편차라도 여러 단계에 걸쳐 영향이 지속되면 심각한 문제로 발전할 수 있다. 장기 평가(Long-Horizon Evaluation)는 각 행동을 독립적인 사건으로 평가하는 대신 오류가 어떻게 발생하고, 상호작용하며, 후속 작업에 영향을 미치는지 검토해야 한다.

오류 전파(Error Propagation)는 한 구성 요소(Component)의 부정확성이 후속 구성 요소의 출력에 영향을 미칠 때 발생한다. 작은 인식 오류(Perception Error)가 상태 추정(State Estimation)에 영향을 미치고, 이는 다시 계획 결정(Planning Decision)과 제어 명령(Control Command)을 변화시킬 수 있다. 그 결과 발생한 물리적 편차(Physical Deviation)는 추가적인 관측 오류를 유발하여 피드백 순환(Feedback Cycle)을 형성할 수 있다. 이러한 과정을 평가하려면 감지(Sensing), 추론(Reasoning), 계획(Planning), 실행(Execution) 사이의 관계를 추적해야 한다.

장기 임무(Long-Horizon Mission)는 중간 상태(Intermediate State)가 후속 행동의 초기 조건(Initial Condition)이 되는 경우가 많기 때문에 오류에 특히 취약하다. 로봇이 물체를 의도한 위치에서 약간 벗어나게 배치하면 이후의 파지(Grasp) 또는 조립 작업(Assembly Operation)이 실패할 수 있다. 초기 배치 오류(Placement Error)는 작아 보이더라도 후속 단계에 미치는 영향(Downstream Consequence)은 상당할 수 있다. 따라서 평가는 즉각적인 오류 크기(Error Magnitude)와 최종 임무 영향(Mission Impact)을 모두 고려해야 한다.

누적 오류(Compounding Error)가 항상 일정한 속도로 증가하는 것은 아니다. 일부 부정확성은 거의 선형적(Linear)으로 누적되지만, 다른 오류는 불안정한 동역학(Unstable Dynamics), 반복적인 추정 편향(Estimation Bias), 상호작용하는 제어 오류(Control Error)로 인해 빠르게 증가한다. 특정 편차는 수정 피드백(Corrective Feedback)을 통해 감소할 수도 있다. 평가는 시간이 지남에 따라 오류가 증폭(Amplification), 유지(Preservation), 감쇠(Attenuation)되는지 식별하고 이러한 현상을 발생시키는 조건을 파악해야 한다.

상태 추정 오류(State Estimation Error)는 장기 성능 저하(Long-Horizon Performance Degradation)의 주요 원인이다. 이동 로봇(Mobile Robot)은 불완전한 측정값을 사용하여 위치(Position), 방향(Orientation), 속도(Velocity), 환경과의 공간적 관계(Environmental Relationship)를 지속적으로 추정한다. 특히 외부 기준 관측(External Reference Observation)을 사용할 수 없는 경우 장시간의 내비게이션(Navigation) 과정에서 작은 위치 추정 오류(Localization Error)가 누적될 수 있다. 평가는 추정 드리프트(Estimation Drift)와 이것이 내비게이션, 조작, 작업 완료에 미치는 영향을 측정해야 한다.

인식 오류(Perception Error)는 환경의 기호적 표현(Symbolic Representation)과 기하학적 표현(Geometric Representation)을 통해 전파될 수 있다. 물체를 잘못 식별하거나 자세(Pose)를 부정확하게 추정하거나 장애물을 놓치면 부정확한 세계 모델(World Model)이 생성될 수 있다. 이러한 표현을 기반으로 작동하는 계획 시스템(Planning System)은 내부적으로는 일관되지만 물리적으로는 부적절한 행동을 생성할 수 있다. 평가는 잘못된 관측(Incorrect Observation)으로 인한 실패와 후속 추론(Subsequent Reasoning)으로 인한 실패를 구분해야 한다.

제어 부정확성(Control Inaccuracy)은 오류 누적의 또 다른 경로를 형성한다. 액추에이터 지연(Actuator Delay), 보정 오류(Calibration Error), 마찰 변화(Friction Variation), 불완전한 동역학 모델(Imperfect Dynamics Model)은 명령된 움직임(Commanded Motion)과 실제 움직임(Actual Motion) 사이에 차이를 발생시킬 수 있다. 반복 실행은 위치 편차(Positional Deviation)를 증가시키거나 물체와의 불안정한 상호작용(Unstable Interaction)을 유발할 수 있다. 평가는 물리적 불확실성(Physical Uncertainty)과 외란(Disturbance)을 고려하면서 의도한 궤적(Intended Trajectory)과 관측된 궤적(Observed Trajectory)을 비교해야 한다.

개별 행동이 정확하게 실행되더라도 계획 오류(Planning Error)는 누적될 수 있다. 잘못된 작업 분해(Task Decomposition), 누락된 선행 조건(Prerequisite), 부적절한 행동 순서(Action Ordering)는 해결하기 점점 어려워지는 의존성(Dependency)을 만들어 낼 수 있다. 로봇은 국소적으로 유효한 작업을 여러 개 완료하면서도 전체 임무 목표(Overall Mission Objective)에서는 점점 멀어질 수 있다. 평가는 계획 결정이 미래의 실행 가능성(Future Feasibility)을 유지하고 지속적인 진행(Sustained Progress)을 지원하는지 검토해야 한다.

기억 및 맥락 오류(Memory and Context Error)도 장기 임무 실패에 영향을 미친다. 로봇은 하위 작업(Subtask)이 완료되었다는 사실을 잊거나, 물체에 대한 오래된 정보(Outdated Information)를 유지하거나, 현재 임무 단계(Current Mission Stage)를 이전 단계와 혼동할 수 있다. 이러한 오류는 중복 행동(Redundant Action), 잘못된 상태 전환(Incorrect Transition), 안전하지 않은 의사결정(Unsafe Decision)을 유발할 수 있다. 평가는 시스템이 장시간 실행 과정에서 작업 관련 정보(Task-Relevant Information)를 얼마나 안정적으로 보존하고 갱신하는지 확인해야 한다.

국소 정확도(Local Accuracy)와 전체 신뢰성(Global Reliability) 사이의 관계는 누적 오류 분석(Compounding-Error Analysis)의 핵심이다. 시스템은 개별 기술(Individual Skill)에서는 높은 성공률을 달성하더라도 긴 작업 시퀀스(Long Task Sequence)에서는 훨씬 낮은 임무 완료율(Mission Completion Rate)을 보일 수 있다. 단순화된 독립성 가정(Independence Assumption)에서는 반복 작업의 성공 확률이 단계별로 곱해진다. 실제 시스템에서는 오류가 상관관계(Correlation)를 가지거나 복구 가능(Recoverable)하거나 공통 환경 조건(Shared Environmental Condition)에 의존할 수 있으므로 추가 분석이 필요하다.

오류 상관관계(Error Correlation)는 장기 임무 결과에 상당한 영향을 미칠 수 있다. 반복적인 실패는 독립적인 무작위 외란(Random Disturbance)이 아니라 지속적인 보정 편향(Calibration Bias), 잘못된 세계 모델(Incorrect World Model), 공통 센서 한계(Shared Sensor Limitation)에서 발생할 수 있다. 이러한 오류는 여러 하위 작업에 유사한 방식으로 영향을 미칠 수 있다. 평가는 공통 실패 원인(Common Failure Source)을 식별하고 체계적 오류(Systematic Error)와 확률적 변동(Stochastic Variation)을 구분하여 잘못된 신뢰성 추정(Reliability Estimate)을 방지해야 한다.

오류 전파(Error Propagation)는 관측(Observation), 내부 상태(Internal State), 의사결정(Decision), 물리적 결과(Physical Outcome) 사이의 시간적 의존성(Temporal Dependency)을 통해 표현할 수 있다. 상세한 실행 로그(Execution Log)를 활용하면 평가자는 편차가 처음 발생한 시점과 이후 단계에 미친 영향을 재구성할 수 있다. 타임스탬프가 포함된 센서 데이터(Timestamped Sensor Data), 상태 추정값(State Estimate), 계획된 행동(Planned Action), 제어 출력(Control Output), 검증 결과(Verification Result)는 실패 전파 경로(Failure Pathway)를 진단하고 잠재적인 개입 지점(Intervention Point)을 식별하는 근거를 제공한다.

정량적 오류 지표(Quantitative Error Metrics)는 편차의 물리적 중요성(Physical Significance)과 운영상 중요성(Operational Significance)을 반영해야 한다. 위치 오류(Position Error), 방향 오류(Orientation Error), 궤적 편차(Trajectory Deviation), 상태 추정 불확실성(State Estimation Uncertainty), 작업 제약 조건 위반(Task Constraint Violation)이 모두 관련될 수 있다. 그러나 동일한 수치적 오류(Numerical Error)라도 작업에 따라 결과가 달라질 수 있다. 작은 위치 편차는 내비게이션에서는 문제가 없을 수 있지만 정밀 조립(Precision Assembly)에서는 허용되지 않을 수 있다.

오류 예산(Error Budget)은 시스템 구성 요소와 작업 단계 전반에 허용 가능한 불확실성(Acceptable Uncertainty)을 할당하는 구조화된 방법을 제공한다. 임무는 감지(Sensing), 위치 추정(Localization), 조작(Manipulation), 최종 배치(Final Placement)에 대한 허용 오차(Tolerance)를 지정할 수 있다. 평가는 개별 구성 요소가 할당된 한계(Assigned Limit) 내에서 작동하는지, 결합된 오류(Combined Error)가 임무 요구 사항(Mission Requirement)을 위협하는지 판단할 수 있다. 이러한 오류 예산은 모든 오류 원인이 독립적으로 기여한다고 가정하는 대신 상호 의존성을 고려해야 한다.

복구 및 수정 메커니즘(Recovery and Correction Mechanism)은 누적된 오류가 최종 실패(Terminal Failure)로 이어지는지를 결정한다. 재보정(Recalibration), 능동 인식(Active Perception), 위치 추정 갱신(Localization Update), 재계획(Replanning), 수정 조작(Corrective Manipulation)은 편차가 추가로 전파되기 전에 이를 감소시킬 수 있다. 평가는 시스템이 오류를 얼마나 빠르게 감지하는지, 수정 행동(Corrective Action)이 유효한 상태(Valid State)를 복원하는지, 복구 이후 잔여 불확실성(Residual Uncertainty)이 얼마나 남아 있는지 측정해야 한다.

조기 오류 감지(Early Error Detection)는 실행이 진행될수록 수정 비용(Correction Cost)이 증가하는 경우가 많기 때문에 특히 중요하다. 잘못 배치된 부품(Misplaced Component)은 즉시 위치를 수정하기 쉽지만 추가 조립 단계가 진행된 후에는 접근하기 어려울 수 있다. 마찬가지로 위치 추정 드리프트(Localization Drift)는 제한된 작업 공간(Constrained Workspace)에 진입하기 전에 수정할 수 있지만 정밀 이동(Precision Movement) 중에는 위험해질 수 있다. 평가는 감지 지연 시간(Detection Latency)과 개입 지연(Delayed Intervention)의 운영상 결과를 검토해야 한다.

장기 오류 분석(Long-Horizon Error Analysis)은 불확실성 누적(Uncertainty Accumulation)도 고려해야 한다. 로봇은 겉으로는 일관된 추정 상태(Estimated State)를 유지하면서도 해당 추정값에 대한 신뢰도(Confidence)가 점진적으로 감소할 수 있다. 적절한 불확실성 추적(Uncertainty Tracking)이 없으면 계획 시스템은 정당화되지 않은 가정(Unjustified Assumption)에 기반하여 계속 작동할 수 있다. 평가는 불확실성 추정값(Uncertainty Estimate)이 적절하게 보정되어 있는지, 신뢰도가 충분하지 않을 때 시스템이 추가 관측(Additional Observation)을 요청하는지 확인해야 한다.

시뮬레이션(Simulation)은 알려진 외란(Known Disturbance)을 도입하고 그 크기(Magnitude), 발생 시점(Timing), 빈도(Frequency)를 변화시킴으로써 오류 전파를 연구할 수 있는 통제된 환경을 제공한다. 연구자는 센서 잡음(Sensor Noise), 액추에이터 편향(Actuator Bias), 지연된 관측(Delayed Observation), 잘못된 물체 자세(Incorrect Object Pose)를 주입하여 시스템 민감도(System Sensitivity)를 식별할 수 있다. 그러나 실제 접촉 동역학(Real-World Contact Dynamics)과 환경 변동성(Environmental Variability)이 시뮬레이션과 상당히 다를 수 있으므로 시뮬레이션의 오류 거동(Error Behavior)은 물리적 측정(Physical Measurement)을 통해 검증해야 한다.

벤치마크 절차(Benchmark Protocol)는 실행 범위(Execution Horizon)에 따라 신뢰성이 어떻게 변화하는지 확인할 수 있도록 길이와 복잡도가 다양한 임무를 포함해야 한다. 반복 시험(Repeated Trial)을 통해 실패 확률(Failure Probability), 누적 편차(Accumulated Deviation), 복구 빈도(Recovery Frequency), 최종 실패까지의 시간(Time to Terminal Failure)을 측정할 수 있다. 비교에서는 작업 난이도(Task Difficulty)와 외란 노출(Disturbance Exposure)을 통제해야 한다. 최종 성공률(Final Success Rate)과 함께 오류 궤적(Error Trajectory)을 보고하면 종합 완료 통계(Aggregate Completion Statistics)만 사용하는 것보다 더 많은 진단 정보를 제공할 수 있다.

안전 필수 오류 전파(Safety-Critical Error Propagation)는 작은 편차가 결국 엄격한 운영 제약 조건(Hard Operational Constraint)을 위반할 수 있기 때문에 특별한 주의가 필요하다. 누적되는 위치 추정 오류(Localization Error)는 장애물 이격 거리(Obstacle Clearance)를 감소시킬 수 있으며, 반복적인 힘 제어 부정확성(Force-Control Inaccuracy)은 취약한 물체(Fragile Object)를 손상시킬 수 있다. 평가는 안전 여유(Safety Margin)를 식별하고, 제약 조건 경계(Constraint Boundary)에 접근하는 상황을 감시하며, 복구 가능한 편차(Recoverable Deviation)와 즉각적인 개입이 필요한 위험 상태(Hazardous State)를 구분해야 한다.

포괄적인 프레임워크(Comprehensive Framework)는 오류 원인(Error Source), 전파 경로(Propagation Pathway), 감지 메커니즘(Detection Mechanism), 최종 임무 결과(Final Mission Consequence)를 연결해야 한다. 인식(Perception), 추정(Estimation), 기억(Memory), 계획(Planning), 제어(Control)를 독립적인 하위 시스템(Subsystem)이 아니라 상호작용하는 구성 요소(Interacting Component)로 분석해야 한다. 궁극적으로 누적 오류(Compounding Error)에 대한 이해는 피지컬 인공지능(Physical AI) 개발자가 편차를 조기에 감지하고, 오류 증폭(Error Amplification)을 제한하며, 현실적인 불확실성(Realistic Uncertainty) 속에서도 신뢰할 수 있는 장기 운영(Reliable Long-Horizon Operation)을 지속하는 시스템을 설계할 수 있도록 한다.

## 06.07. Memory and Context Retention

![](images/image7.png){width="7.268055555555556in" height="7.268055555555556in"}

기억 및 맥락 유지(Memory and Context Retention)는 피지컬 인공지능(Physical AI) 시스템이 장시간의 작업 실행 과정에서 일관된 의사결정(Coherent Decision-Making)에 필요한 정보를 보존하고, 검색하고, 갱신하는 능력을 의미한다. 단기 작업(Short-Horizon Task)과 달리 장기 임무(Long-Horizon Mission)는 시간적으로 멀리 떨어진 시점에 이루어진 관측과 의사결정에 의존한다. 평가는 시스템이 관련 정보를 유지하면서 오래되거나 중복되거나 오해를 유발하는 표현을 방지하는지 확인해야 한다.

기억(Memory)은 로봇이 이전 경험(Previous Experience)을 현재 관측(Current Observation) 및 미래 목표(Future Objective)와 연결할 수 있도록 한다. 로봇은 물체가 마지막으로 관측된 위치, 완료된 하위 작업(Subtask), 여전히 유효한 환경 제약 조건(Environmental Constraint)을 기억해야 할 수 있다. 신뢰할 수 있는 기억 유지(Reliable Retention)가 없으면 시스템은 완료된 행동을 반복하거나 필수적인 의존성(Dependency)을 놓칠 수 있다. 장기 평가(Long-Horizon Evaluation)는 저장된 정보가 일관된 임무 실행(Consistent Mission Execution)을 지원하는지 평가해야 한다.

맥락 유지(Context Retention)는 개별 관측 정보를 저장하는 것 이상의 의미를 갖는다. 이는 임무 목표(Mission Objective), 작업 지시(Task Instruction), 환경 상태(Environmental State), 이전 의사결정(Earlier Decision) 사이의 관계를 보존하는 것을 포함한다. 로봇은 물체의 위치를 기억하면서도 해당 물체가 선택된 이유나 현재 작업과의 관계를 잊을 수 있다. 평가는 유지된 맥락이 단순히 분리된 과거 정보를 재현하는 데 그치지 않고 의미 있는 추론(Meaningful Reasoning)을 지원하는지 검토해야 한다.

서로 다른 시간적 규모(Temporal Scale)는 서로 다른 형태의 기억을 필요로 한다. 단기 기억(Short-Term Memory)은 즉각적인 인식과 제어를 지원하고, 중기 기억(Medium-Term Memory)은 하위 목표의 진행 상황과 국소 작업 맥락(Local Task Context)을 유지하며, 장기 기억(Long-Term Memory)은 지속적인 환경 지식(Persistent Environmental Knowledge)과 이전 경험을 보존한다. 이러한 계층은 모순을 발생시키지 않으면서 정보를 교환해야 한다. 평가는 실행 시간 범위(Execution Horizon)가 변화하더라도 관련 지식에 접근할 수 있는지 확인해야 한다.

작업 기억(Working Memory)은 즉각적인 의사결정에 필요한 활성 정보(Active Information)를 제공한다. 여기에는 현재 로봇 상태(Robot State), 주변 장애물(Nearby Obstacle), 활성 지시(Active Instruction), 최근 관측된 물체 속성(Object Property)이 포함될 수 있다. 컴퓨팅 용량(Computational Capacity)이 제한되어 있으므로 시스템은 현재 행동에 직접적인 영향을 미치는 정보를 우선적으로 유지해야 한다. 평가는 작업 기억이 필수적인 세부 정보를 보존하면서 실행에 더 이상 기여하지 않는 정보를 제거하는지 측정해야 한다.

일화 기억(Episodic Memory)은 특정 시간과 상황에 연관된 사건과 경험을 기록한다. 로봇은 물체가 가려져 파지(Grasp)에 실패했거나 이전 시도에서 복도에 접근할 수 없게 되었던 사실을 기억할 수 있다. 이러한 기록은 복구(Recovery)와 향후 계획(Future Planning)을 지원할 수 있다. 평가는 시스템이 관련 경험을 정확하게 검색하고 과거 조건을 현재 현실과 혼동하지 않으면서 그 경험에서 얻은 교훈을 적용하는지 검토해야 한다.

의미 기억(Semantic Memory)은 물체, 환경, 절차, 운영 규칙(Operational Rule)에 관한 보다 지속적인 지식을 표현한다. 로봇은 여러 임무에 걸쳐 도구의 기능(Tool Function), 공간 간 관계(Room Relationship), 취급 요구 사항(Handling Requirement)에 관한 정보를 유지할 수 있다. 그러나 환경이 변화하면 지속적으로 보존된 지식도 부정확해질 수 있다. 평가는 의미 정보(Semantic Information)가 계속 유용한지, 시스템이 안정적인 지식(Stable Knowledge)과 검증이 필요한 가정(Assumption)을 구분하는지 확인해야 한다.

절차 기억(Procedural Memory)은 학습된 기술(Skill)과 행동 시퀀스(Action Sequence)의 재사용을 지원한다. 로봇은 반복 작업에서 계획 부담(Planning Effort)을 줄일 수 있는 성공적인 조작 절차(Manipulation Routine), 내비게이션 전략(Navigation Strategy), 복구 절차(Recovery Procedure)를 유지할 수 있다. 평가는 이러한 절차가 변화하는 조건에서도 효과적인지 판단해야 한다. 성공적인 기억 유지는 다른 환경에서 학습한 행동을 무조건 반복하는 것이 아니라 적절한 적응(Adaptation)을 요구한다.

기억 검색(Memory Retrieval)은 기억 저장(Memory Storage)만큼 중요하다. 시스템이 정확한 정보를 보존하고 있더라도 관련 의사결정이 필요한 시점에 해당 정보를 검색하지 못할 수 있다. 검색 메커니즘(Retrieval Mechanism)은 현재 목표(Current Goal), 환경 맥락(Environmental Context), 시간적 관련성(Temporal Relevance)을 기반으로 작업 관련 기록(Task-Related Record)을 식별해야 한다. 평가는 관련 없는 내용을 도입하지 않으면서 방대한 이력에서 유용한 정보를 선택하는 능력과 검색 정확도(Retrieval Accuracy), 검색 지연 시간(Retrieval Latency)을 측정해야 한다.

기억 갱신(Memory Updating)은 저장된 정보가 새로운 관측과 충돌할 수 있기 때문에 또 다른 과제를 제시한다. 이전에 특정 위치에 있다고 기록된 물체가 이동했거나 환경 외란(Environmental Disturbance)으로 인해 완료된 하위 목표(Subgoal)가 무효화될 수 있다. 유능한 시스템은 유용한 과거 증거(Historical Evidence)를 보존하면서 내부 표현(Internal Representation)을 수정해야 한다. 평가는 적절한 갱신(Appropriate Update)과 우발적인 망각(Accidental Forgetting), 신뢰할 수 있는 정보의 정당화되지 않은 대체(Unjustified Replacement)를 구분해야 한다.

맥락 창(Context Window)과 컴퓨팅 한계(Computational Limit)는 동시에 처리할 수 있는 과거 정보의 양을 제한한다. 트랜스포머 기반 추론(Transformer-Based Reasoning)을 사용하는 시스템은 장기간의 이력을 관리하기 위해 요약(Summarization), 검색(Retrieval), 계층적 표현(Hierarchical Representation)이 필요할 수 있다. 압축(Compression)은 자원 소비를 줄이지만 중요한 의존성이나 안전 조건(Safety Condition)을 제거할 수 있다. 평가는 압축된 맥락(Compressed Context)이 이후 의사결정에 필수적인 정보를 보존하는지 확인해야 한다.

계층적 기억 구조(Hierarchical Memory Organization)는 즉각적인 관측(Immediate Observation), 작업 수준 요약(Task-Level Summary), 지속적 지식(Persistent Knowledge)을 분리하여 확장성(Scalability)을 개선할 수 있다. 상위 수준 표현(High-Level Representation)은 임무 목표와 의존성을 포착하고, 하위 수준 기록(Lower-Level Record)은 상세한 실행 증거(Execution Evidence)를 보존한다. 정보는 운영상 관련성(Operational Relevance)에 따라 계층 사이를 이동해야 한다. 평가는 추상화(Abstraction)가 핵심 세부 정보를 보존하는지, 필요할 때 상세 기록을 복구할 수 있는지 시험해야 한다.

시간적 일관성(Temporal Consistency)은 기억된 정보마다 유효 기간(Validity Period)이 다르기 때문에 필수적이다. 고정된 출입구에 관한 로봇의 지식은 수개월 동안 유용할 수 있지만 움직이는 사람에 대한 관측은 몇 초 만에 오래된 정보가 될 수 있다. 기억 시스템(Memory System)은 정보에 타임스탬프(Timestamp), 신뢰도 추정값(Confidence Estimate), 유효성 조건(Validity Condition)을 연결해야 한다. 평가는 로봇이 저장된 정보에 대한 재관측(Renewed Observation)이 필요한 시점을 인식하는지 판단해야 한다.

장기 임무(Long-Horizon Mission)는 목표 및 지시의 연속성(Goal and Instruction Continuity)도 유지해야 한다. 로봇은 초기 목표(Initial Objective)를 받은 후 작업 중단(Interruption)을 경험하고, 복구 작업(Recovery Operation)을 수행한 다음 원래 작업을 재개할 수 있다. 시스템은 필수 제약 조건(Mandatory Constraint)을 보존하고 일시적인 복구 목표(Temporary Recovery Goal)와 주요 임무(Primary Mission)를 구분해야 한다. 평가는 장시간 실행으로 인해 목표 이탈(Goal Drift), 요구 사항 망각(Forgotten Requirement), 부적절한 작업 우선순위 변경(Inappropriate Task Priority Change)이 발생하는지 식별해야 한다.

기억 실패(Memory Failure)는 계획 및 제어 오류(Planning and Control Error)로 전파될 수 있다. 물체를 이미 운반했다는 사실을 잊으면 중복 취급(Duplicate Handling)이 발생할 수 있으며, 오래된 장애물 지도(Outdated Obstacle Map)를 유지하면 안전하지 않은 내비게이션 결정(Unsafe Navigation Decision)이 생성될 수 있다. 이러한 실패는 근본적인 문제가 잘못된 기억(Incorrect Memory)에 있음에도 후속 구성 요소(Downstream Component)에서 발생한 것처럼 보일 수 있다. 평가는 이러한 의존성을 추적하여 기억 유지 실패(Retention Failure)와 추론 또는 실행 실패(Reasoning or Execution Failure)를 구분해야 한다.

견고한 기억 평가(Robust Memory Evaluation)를 위해서는 정보 획득(Information Acquisition)과 이후 활용(Later Use)을 의도적으로 분리하는 시험이 필요하다. 벤치마크(Benchmark)는 임무 초기에 물체의 속성(Object Property)을 제시하고 여러 개의 관련 없는 하위 작업 이후 로봇이 이를 적용하도록 요구할 수 있다. 지연 시간(Delay), 중간 활동(Intervening Activity), 환경 변화(Environmental Change)를 다양하게 설정하면 기억 유지의 한계(Retention Limitation)를 파악할 수 있다. 성공은 원래 관측에 반복적으로 접근하는 것이 아니라 기억된 정보를 적절하게 활용하는 데 기반해야 한다.

정량적 지표(Quantitative Metrics)에는 기억 유지 정확도(Retention Accuracy), 검색 정밀도(Retrieval Precision), 갱신 정확성(Update Correctness), 맥락 일관성(Context Consistency), 기억 관련 작업 성공률(Memory-Related Task Success)이 포함될 수 있다. 검색 지연 시간(Retrieval Latency)과 컴퓨팅 오버헤드(Computational Overhead)도 실시간 운영(Real-Time Operation)에 중요하다. 그러나 독립적인 기억 점수(Isolated Memory Score)가 실제 운영상의 유용성(Operational Usefulness)을 반영하지 못할 수 있다. 평가는 기억 성능을 후속 계획 품질(Downstream Planning Quality), 복구 효과(Recovery Effectiveness), 최종 임무 결과(Final Mission Outcome)와 연결해야 한다.

기억된 정보가 항상 신뢰할 수 있는 것은 아니므로 불확실성 관리(Uncertainty Management)가 필요하다. 센서 잡음(Sensor Noise), 불완전한 관측(Incomplete Observation), 모호한 사건(Ambiguous Event)은 불확실한 기록(Uncertain Record)을 생성할 수 있다. 로봇은 검증된 사실(Verified Fact)과 추정값(Estimate)을 구분하고 신뢰도가 낮은 기억(Low-Confidence Memory)을 권위 있는 정보로 취급하지 않아야 한다. 평가는 특히 안전 필수 의사결정(Safety-Critical Decision)이 과거 정보에 의존하는 경우 저장, 검색, 요약, 갱신 과정에서 불확실성이 유지되는지 확인해야 한다.

인간 개입(Human Intervention)과 다중 에이전트 협력(Multi-Agent Coordination)은 추가적인 맥락 요구 사항(Context Requirement)을 발생시킨다. 로봇은 운영자(Operator)로부터 수정된 지시(Corrected Instruction)를 받거나 다른 로봇과 작업 정보(Task Information)를 교환할 수 있다. 이러한 갱신은 이전 의사결정의 이력을 잃거나 정보 출처(Information Source)를 혼동하지 않으면서 통합되어야 한다. 평가는 출처 귀속(Source Attribution), 지시 우선순위(Instruction Precedence), 공유 기억(Shared Memory)과 로컬 기억(Local Memory) 사이의 일관성을 검증해야 한다.

벤치마크 절차(Benchmark Protocol)는 작업 중단(Interruption), 반복적으로 등장하는 물체(Repeated Object), 변화하는 환경(Changing Environment), 지연된 의존성(Delayed Dependency)을 포함하는 장기 임무를 다루어야 한다. 평가 로그(Evaluation Log)는 기억 쓰기(Memory Write), 검색 이벤트(Retrieval Event), 갱신(Update), 타임스탬프(Timestamp), 그에 따른 의사결정(Resulting Decision)을 보존해야 한다. 통제된 실험(Controlled Experiment)은 동일한 조건에서 서로 다른 기억 아키텍처(Memory Architecture)를 사용하는 시스템을 비교할 수 있다. 기억 전용 지표(Memory-Specific Metrics)와 임무 수준 결과(Mission-Level Outcome)를 함께 보고하면 아키텍처 개선이 실질적인 자율성(Practical Autonomy)으로 이어지는지 확인할 수 있다.

궁극적으로 기억 및 맥락 유지(Memory and Context Retention)는 신뢰할 수 있는 장기 피지컬 인공지능(Dependable Long-Horizon Physical AI)에 필요한 정보적 연속성(Informational Continuity)을 제공한다. 효과적인 시스템은 관련 경험(Relevant Experience)을 보존하고, 필요할 때 검색하며, 오래된 표현(Outdated Representation)을 갱신하고, 장시간 실행 과정에서 일관된 목표(Consistent Objective)를 유지해야 한다. 이러한 역량을 평가하면 로봇이 각각의 관측과 행동을 독립적인 사건으로 취급하는 데 그치지 않고 시간에 걸쳐 일관되게 추론(Coherent Reasoning)할 수 있는지 확인할 수 있다.

## 06.08. World State Consistency over Time

![](images/image8.png){width="7.268055555555556in" height="7.268055555555556in"}

시간에 따른 세계 상태 일관성(World State Consistency over Time)은 피지컬 인공지능(Physical AI) 시스템이 장시간의 작업 실행 과정에서 환경에 대한 정확하고 일관된 표현(Representation)을 유지하는 능력을 의미한다. 로봇이 관측하고, 이동하고, 물체를 조작하고, 사람과 상호작용하는 동안 물리적 세계(Physical World)는 지속적으로 변화한다. 평가는 내부 세계 상태(Internal World State)가 모순을 발생시키거나 필수 정보를 잃거나 유효하지 않은 가정을 유지하지 않으면서 이러한 변화를 반영하는지 확인해야 한다.

세계 상태 표현(World State Representation)은 로봇, 물체, 위치 및 이들 사이의 관계에 대한 관련 속성을 설명한다. 여기에는 물체 식별 정보(Object Identity), 위치(Position), 방향(Orientation), 접근 가능성(Accessibility), 점유 상태(Occupancy), 작업 관련 조건(Task-Related Condition)이 포함될 수 있다. 장기 임무(Long-Horizon Mission)에서는 이러한 속성이 로봇의 행동과 외부 사건(External Event)에 따라 변화한다. 일관성(Consistency)을 유지하려면 시스템이 지속적인 사실(Persistent Fact)과 일시적인 관측(Temporary Observation)을 구분하고 각 속성을 예상되는 동역학(Expected Dynamics)에 따라 갱신해야 한다.

시간적 일관성(Temporal Consistency)은 순간적인 인식 정확도(Instantaneous Perception Accuracy)와 다르다. 로봇이 개별 이미지에서 물체를 정확하게 식별하더라도 연속적인 관측 사이에서 물체 위치에 대한 모순된 믿음(Belief)을 유지할 수 있다. 마찬가지로 장애물 뒤에 일시적으로 가려진 물체가 내부 표현에서 자동으로 사라져서는 안 된다. 평가는 개별 관측만 평가하는 대신 정보가 시간에 걸쳐 논리적·물리적으로 일관되게 유지되는지 검토해야 한다.

상태 전이(State Transition)는 시간적 일관성을 평가하기 위한 기반을 제공한다. 각 행동(Action)이나 외부 사건은 세계를 하나의 구성 상태(Configuration)에서 다른 상태로 변화시킬 수 있다. 로봇이 물체를 파지하면 물체의 부착 상태(Attachment State)와 변화하는 위치를 반영하도록 내부 표현을 갱신해야 한다. 평가는 예측된 상태 전이(Predicted Transition)와 관측된 결과(Observed Outcome)를 비교하고 예상하지 못한 차이가 발생했을 때 적절한 상태 수정(State Revision)이 이루어지는지 판단해야 한다.

물체 영속성(Object Permanence)은 부분 관측 가능성(Partial Observability) 환경에서 추론하기 위한 필수 요소이다. 물리적 물체는 일반적으로 센서의 시야(Field of View)에서 벗어나더라도 계속 존재하지만, 현재 위치에 대한 불확실성(Uncertainty)은 증가할 수 있다. 로봇은 물체의 식별 정보(Object Identity)를 유지하면서 현재 상태에 대한 신뢰도(Confidence)를 조정해야 한다. 평가는 시스템이 근거 없는 움직임을 만들어 내거나 관측되지 않은 조건을 검증된 사실로 취급하지 않으면서 타당한 물체 이력(Object History)을 유지하는지 시험해야 한다.

식별 정보 일관성(Identity Consistency)은 동일한 환경에 여러 개의 유사한 물체가 존재할 때 유지하기 어려워진다. 로봇은 일시적인 가림(Occlusion)이나 위치 변경(Relocation) 이후 동일한 형태의 용기(Container), 도구(Tool), 부품(Component)을 혼동할 수 있다. 이러한 오류는 잘못된 조작(Incorrect Manipulation)과 작업 완료 판단(Task Completion Decision)으로 전파될 수 있다. 평가는 임무 전반에서 물체의 식별 정보가 올바른 이력, 속성(Attribute), 의도된 목적지(Intended Destination)와 연결되어 유지되는지 측정해야 한다.

공간적 일관성(Spatial Consistency)은 좌표계(Coordinate Frame), 물체 자세(Object Pose), 로봇 위치 추정(Robot Localization), 환경 지도(Environmental Map) 사이의 일관된 관계를 요구한다. 작은 보정 오류(Calibration Error)나 위치 추정 오류(Localization Error)는 동일한 물체가 시간에 따라 서로 양립할 수 없는 위치에 나타나게 할 수 있다. 평가는 좌표 변환(Coordinate Transformation), 누적 드리프트(Accumulated Drift), 지도 정렬(Map Alignment)을 검토해야 한다. 신뢰할 수 있는 시스템은 실제 물체 이동(Actual Object Movement)과 추정 부정확성(Estimation Inaccuracy)으로 인한 겉보기 이동(Apparent Movement)을 구분해야 한다.

의미적 일관성(Semantic Consistency)은 물체, 위치, 작업 조건에 부여된 의미와 관련된다. 비어 있다고 분류된 용기(Container)가 불확실성이나 상충하는 증거(Conflicting Evidence)를 명시적으로 모델링하지 않는 한 동시에 물품을 담고 있는 것으로 표현되어서는 안 된다. 마찬가지로 완료된 배송(Completed Delivery)은 검증된 전달 조건(Verified Transfer Condition)에 대응해야 한다. 평가는 모순된 의미적 주장(Semantic Assertion)을 식별하고 시스템이 관측이나 추론을 통해 이러한 모순을 해결하는지 판단해야 한다.

장기 세계 모델(Long-Horizon World Model)은 로봇에 의해 발생한 변화(Robot-Induced Change)와 외부에서 발생한 변화(Externally Induced Change)를 모두 고려해야 한다. 로봇은 의도적으로 물체를 이동시킬 수 있으며, 사람은 로봇이 관측하지 못한 상태에서 다른 물체의 위치를 변경할 수 있다. 이후 관측이 저장된 정보와 충돌하면 시스템은 가능한 외부 변화를 고려해야 한다. 평가는 수정된 표현이 물리적으로 타당한지, 정당화되지 않은 가정을 사용하지 않으면서 불확실성을 처리하는지 확인해야 한다.

시간적 유효성(Temporal Validity)은 세계 상태 정보(World State Information)의 또 다른 핵심 속성이다. 고정된 벽의 위치는 장기간 신뢰할 수 있지만 움직이는 사람의 위치는 거의 즉시 오래된 정보가 될 수 있다. 상태 표현(State Representation)은 관측에 타임스탬프(Timestamp), 신뢰도 수준(Confidence Level), 예상 변화율(Expected Rate of Change)을 연결해야 한다. 평가는 시스템이 오래된 정보(Stale Information)를 인식하고 중요한 행동을 수행하기 전에 갱신된 관측(Updated Observation)을 요청하는지 판단해야 한다.

예측 일관성(Prediction Consistency)은 현재 세계 상태(Current World State)를 예상되는 미래 변화(Expected Future Development)와 연결한다. 피지컬 인공지능 시스템은 학습 기반 동역학 모델(Learned Dynamics Model)이나 물리 기반 동역학 모델(Physics-Based Dynamics Model)을 사용하여 물체 움직임(Object Motion), 접촉 결과(Contact Outcome), 환경 변화(Environmental Change)를 예측할 수 있다. 평가는 서로 다른 시간 범위(Time Horizon)에 걸쳐 예측된 상태(Predicted State)와 후속 관측(Subsequent Observation)을 비교해야 한다. 예측 오류(Prediction Error)는 체계적 편향(Systematic Bias), 불확실성 보정(Uncertainty Calibration), 계획 결정(Planning Decision)에 미치는 영향을 중심으로 분석해야 한다.

불확실성을 고려한 표현(Uncertainty-Aware Representation)은 실제 세계 상태(True World State)를 완전히 관측할 수 있는 경우가 드물기 때문에 필요하다. 로봇은 모호한 조건에 대해 확률 분포(Probability Distribution), 신뢰 구간(Confidence Interval), 복수 가설(Multiple Hypotheses)을 유지할 수 있다. 시간적 일관성은 불확실성이 사라진 것처럼 가정하는 것을 의미하지 않는다. 대신 평가는 증거가 축적됨에 따라 시스템이 믿음(Belief)을 일관되게 갱신하고 근거가 부족한 결론에 대해 과도한 확신(Excessive Confidence)을 피하는지 검토해야 한다.

상태 추정(State Estimation)과 기억(Memory)은 장시간 실행 과정에서 동기화(Synchronization)된 상태를 유지해야 한다. 인식 모듈(Perception Module)이 물체의 위치를 갱신하더라도 계획 모듈(Planning Module)은 이전 표현(Older Representation)을 계속 사용할 수 있다. 이러한 불일치는 개별 구성 요소가 올바르게 작동하더라도 오래된 정보(Obsolete Information)에 기반한 행동을 유발할 수 있다. 평가는 동기화 지연(Synchronization Delay), 충돌하는 상태 버전(Conflicting State Version), 의사결정이 적절한 정보를 참조하는지 조사해야 한다.

작업 수준 일관성(Task-Level Consistency)은 세계 모델(World Model)을 임무 목표(Mission Objective) 및 완료된 하위 목표(Completed Subgoal)와 연결한다. 로봇은 물품이 배송되었다고 기록했지만 실제 물리적 상태(Physical State)는 해당 물품이 여전히 그리퍼(Gripper)에 부착되어 있음을 나타낼 수 있다. 평가는 기호적 작업 상태(Symbolic Task Status)를 검증된 환경 조건(Verified Environmental Condition)과 비교해야 한다. 이를 통해 시스템이 실행된 명령(Issued Command), 예측된 결과(Predicted Outcome), 물리적으로 확인된 성과(Physically Confirmed Accomplishment)를 혼동하는 것을 방지할 수 있다.

모순 감지(Contradiction Detection)는 신뢰할 수 있는 세계 표현(World Representation)을 유지하기 위한 중요한 역량이다. 관측이 이전 추정값(Previous Estimate)과 일치하지 않거나 예측된 상태 전이(Predicted Transition)가 실패하거나 여러 센서가 서로 양립할 수 없는 측정값(Incompatible Measurement)을 제공할 때 충돌이 발생할 수 있다. 견고한 시스템(Robust System)은 이러한 충돌을 식별하고 필요한 경우 추가 증거(Additional Evidence)를 확보해야 한다. 평가는 감지 정확도(Detection Accuracy), 해결 시간(Resolution Time), 해결되지 않은 모순(Unresolved Contradiction)의 결과를 측정해야 한다.

세계 상태 일관성(World State Consistency)은 누적되는 추정 오류(Accumulated Estimation Error)로 인해 점진적으로 저하될 수 있다. 위치 추정 드리프트(Localization Drift), 물체 추적 오류(Object Tracking Error), 부정확한 접촉 모델(Inaccurate Contact Model), 지연된 갱신(Delayed Update)은 각각 작은 편차(Deviation)를 발생시킬 수 있다. 장기 임무에서는 이러한 부정확성이 상호작용하여 내부 모델(Internal Model)과 물리적 현실(Physical Reality) 사이에 상당한 불일치를 초래할 수 있다. 평가는 오류 증가(Error Growth)를 검토하고 상태 수정(State Correction)이 필요한 시점을 식별해야 한다.

복구 메커니즘(Recovery Mechanism)은 예상하지 못한 사건 이후 일관성을 복원하는 데 도움이 된다. 로봇은 물체를 재관측(Reobservation)하거나 알려진 랜드마크(Known Landmark)를 기준으로 위치를 재추정(Relocalization)하거나 국소 지도(Local Map)를 재구성하거나 작업 상태 추정(Task-State Estimate)을 수정할 수 있다. 효과적인 복구(Effective Recovery)는 신뢰할 수 있는 과거 정보(Historical Information)를 버리지 않으면서 관련 표현을 수정해야 한다. 평가는 복구 정확도(Recovery Accuracy), 복구 시간(Recovery Time), 연산 비용(Computational Cost), 후속 행동이 수정된 상태(Corrected State)와 일관되게 유지되는지 측정해야 한다.

벤치마크 설계(Benchmark Design)는 시간적 세계 모델링(Temporal World Modeling)에 도전하는 통제된 변화(Controlled Change)를 도입해야 한다. 물체는 가려진 상태(Occlusion)에서 이동할 수 있고, 장애물은 예상하지 못한 시점에 나타날 수 있으며, 작업 관련 조건(Task-Relevant Condition)은 관측 사이에 변화할 수 있다. 이러한 시나리오는 시스템이 타당한 믿음(Plausible Belief)을 유지하고 새로운 증거가 확보되면 이를 갱신하는지 시험한다. 평가는 실제 상태 추적 역량(Genuine State-Tracking Capability)과 정적인 환경 가정(Static Environmental Assumption)에 의존한 성공을 구분해야 한다.

정량적 지표(Quantitative Metrics)에는 물체 식별 정보 유지(Object Identity Persistence), 상태 전이 정확도(State Transition Accuracy), 공간 드리프트(Spatial Drift), 모순 발생 빈도(Contradiction Frequency), 시간적 유효성(Temporal Validity), 상태 갱신 지연 시간(State Update Latency)이 포함될 수 있다. 추가적인 측정값은 예측 오류(Prediction Error), 불확실성 보정(Uncertainty Calibration), 복구 효과(Recovery Effectiveness)를 평가할 수 있다. 그러나 오류가 운영상 거의 영향을 미치지 않는다면 수치적 일관성(Numerical Consistency)만으로는 충분하지 않다. 평가는 상태 품질(State Quality)을 계획 실행 가능성(Planning Feasibility), 안전성(Safety), 임무 완료(Mission Completion)와 연결해야 한다.

안전 필수 일관성(Safety-Critical Consistency)은 오래되거나 모순된 세계 상태가 위험한 행동(Hazardous Action)으로 이어질 수 있기 때문에 특별한 주의가 필요하다. 작업 공간(Workspace)에 사람이 없다고 잘못 판단한 로봇은 사람 근처에서 움직임을 시작할 수 있으며, 오래된 장애물 지도(Outdated Obstacle Map)는 내비게이션 이격 거리(Navigation Clearance)를 위협할 수 있다. 평가는 불확실하거나 오래된 안전 관련 정보(Safety-Relevant Information)가 근거 없는 안전 가정(Unsupported Assumption of Safety)이 아니라 적절한 예방 조치(Appropriate Precaution)를 유발하는지 검증해야 한다.

포괄적인 평가 프레임워크(Comprehensive Evaluation Framework)는 인식(Perception), 기억(Memory), 추정(Estimation), 예측(Prediction), 계획(Planning), 제어(Control) 전반에서 세계 상태 일관성(World State Consistency)을 검토해야 한다. 개별 관측이 정확한지뿐 아니라 시스템이 물리적 변화(Physical Change)에 대한 일관된 이력(Coherent History)을 보존하는지도 평가해야 한다. 궁극적으로 시간적 세계 상태 일관성(Temporal World State Consistency)은 피지컬 인공지능(Physical AI) 시스템이 변화하는 환경(Evolving Environment)에 대해 신뢰할 수 있게 추론하고, 장기 임무(Long-Horizon Mission) 동안 안전하고 목표 지향적인 행동(Safe, Goal-Directed Behavior)을 지속할 수 있도록 한다.

## 06.09. Long Horizon Planning and Replanning

![](images/image9.png){width="7.268055555555556in" height="7.268055555555556in"}

장기 계획(Long-Horizon Planning)은 복잡한 임무 목표(Complex Mission Objective)를 달성하기 위해 장시간에 걸쳐 행동과 의사결정을 조직하는 과정이다. 피지컬 인공지능(Physical AI)에서 계획은 환경 제약 조건(Environmental Constraint), 자원 제한(Resource Limitation), 불확실성(Uncertainty)을 고려하면서 상위 수준 목표(High-Level Goal)를 실행 가능한 물리적 행동(Executable Physical Behavior)과 연결해야 한다. 평가는 로봇이 장시간 실행 과정에서도 일관성과 효과를 유지하는 실행 가능한 계획(Feasible Plan)을 수립할 수 있는지 판단해야 한다.

단기 계획(Short-Horizon Planning)과 달리 장기 계획(Long-Horizon Planning)은 초기 의사결정 이후 여러 단계가 지난 시점에 나타날 수 있는 결과를 추론해야 한다. 로봇은 최종 목표에 도달하기 전에 도구를 확보하고, 작업 공간을 준비하고, 자재를 운반하고, 조립을 완료해야 할 수 있다. 평가는 시스템이 필요한 선행 조건(Prerequisite)을 식별하고, 적절한 행동 순서(Action Ordering)를 유지하며, 서로 멀리 떨어진 작업 단계 사이의 의존성(Dependency)을 예측하는지 검토해야 한다.

계획 품질(Planning Quality)은 작업 분해(Task Decomposition)의 정확성과 중간 목표(Intermediate Goal)의 표현 방식에 의존한다. 복잡한 임무는 일반적으로 측정 가능한 완료 조건(Completion Condition)과 명시적인 의존 관계(Explicit Dependency)를 갖는 하위 작업(Subtask)으로 나뉜다. 신뢰할 수 있는 계획기(Planner)는 불필요한 반복이나 누락된 작업 없이 이러한 관계를 만족하는 순서를 생성해야 한다. 평가는 논리적으로 유효한 계획(Logically Valid Plan)과 실제 운영 조건에서 물리적으로 실행 가능한 계획(Physically Executable Plan)을 구분해야 한다.

계층적 계획(Hierarchical Planning)은 서로 다른 추상화 수준(Abstraction Level)의 의사결정을 조정하기 위한 실용적인 구조를 제공한다. 전략적 계획(Strategic Planning)은 임무 목표와 주요 단계를 정의하고, 전술적 계획(Tactical Planning)은 중간 행동을 선택하며, 운영적 계획(Operational Planning)은 실행 가능한 움직임을 생성한다. 이러한 수준은 국소적인 조정(Local Adjustment)을 허용하면서도 상호 일관성을 유지해야 한다. 평가는 하위 수준 실행(Lower-Level Execution)이 상위 수준 계획(Higher-Level Plan)에서 설정된 의도와 제약 조건을 보존하는지 판단해야 한다.

재계획(Replanning)은 관측 결과가 기존 계획(Original Plan)이 더 이상 실행 가능하지 않거나 바람직하지 않음을 보여줄 때 필요해진다. 예상하지 못한 장애물(Unexpected Obstacle), 사용할 수 없는 물체(Unavailable Object), 파지 실패(Failed Grasp), 변화하는 인간 활동(Changing Human Activity)은 이전 가정(Earlier Assumption)을 무효화할 수 있다. 유능한 피지컬 인공지능 시스템은 이러한 변화를 인식하고 대체 행동 경로(Alternative Course of Action)를 생성해야 한다. 평가는 재계획이 의미 있는 환경 변화에 대응하는지, 정당한 이유 없이 계획을 반복적으로 수정하지는 않는지 검토해야 한다.

효과적인 재계획(Effective Replanning)은 어떤 가정이나 제약 조건이 변경되었는지 식별하는 것에서 시작한다. 로봇이 막힌 복도(Blocked Corridor)를 발견하면 전체 임무를 다시 검토하기 전에 대체 경로(Alternative Route)가 존재하는지 판단해야 한다. 마찬가지로 조작 실패(Manipulation Failure)는 작업 전체를 다시 분해하기보다 다른 파지 구성(Grasp Configuration)을 요구할 수 있다. 평가는 시스템이 적절한 수정 범위(Scope of Revision)를 선택하고 이미 완료된 작업에 대한 불필요한 변경을 방지하는지 평가해야 한다.

계획 안정성(Plan Stability)은 과도한 재계획이 효율성을 낮추고 일관되지 않은 행동을 유발할 수 있기 때문에 중요한 고려 사항이다. 사소한 센서 변동(Sensor Fluctuation)이 발생할 때마다 예정된 경로를 변경하는 로봇은 진전을 이루지 못한 채 대안 사이에서 진동(Oscillation)할 수 있다. 평가는 재계획 빈도(Replanning Frequency), 의사결정 안정성(Decision Stability), 계획 수정 규모(Magnitude of Plan Revision)를 측정해야 한다. 신뢰할 수 있는 시스템은 실제 변화에 대한 대응성(Responsiveness)과 관련 없는 외란(Irrelevant Disturbance)에 대한 저항성(Resistance) 사이에서 균형을 유지해야 한다.

불확실성 하의 계획(Planning under Uncertainty)은 물체, 환경, 미래 사건에 관한 불완전한 지식(Incomplete Knowledge)을 표현해야 한다. 로봇은 통로가 계속 접근 가능한지 또는 필요한 부품이 예상 위치에 존재하는지 알지 못할 수 있다. 견고한 계획(Robust Planning)은 불확실성 추정값(Uncertainty Estimate)을 반영하고 가능한 여러 조건에서도 유용한 행동을 선택해야 한다. 평가는 불확실성을 근거 없는 가정(Unsupported Assumption) 뒤에 숨기는 대신 명시적으로 처리하는지 판단해야 한다.

비상 대응 계획(Contingency Planning)은 실패가 발생하기 전에 대체 대응 방안(Alternative Response)을 준비한다. 로봇은 초기 계획 과정에서 예비 경로(Backup Route), 대체 파지 전략(Alternative Grasp Strategy), 대체 자원(Replacement Resource)을 식별할 수 있다. 이러한 준비는 예상하지 못한 사건이 발생했을 때 복구 지연(Recovery Delay)을 줄일 수 있다. 그러나 지나치게 많은 대안을 유지하면 연산 오버헤드(Computational Overhead)가 증가할 수 있다. 평가는 비상 대응 계획이 과도한 계획 비용(Planning Cost)을 발생시키지 않으면서 임무 신뢰성(Mission Reliability)을 향상하는지 검토해야 한다.

장기 계획(Long-Horizon Planning)은 작업 중단(Interruption)과 조건 변화에도 목표 일관성(Goal Consistency)을 유지해야 한다. 로봇은 원래 임무 목표(Original Mission Objective)를 유지하면서 일시적으로 장애물 회피(Obstacle Avoidance), 위치 추정 복구(Localization Recovery), 배터리 충전(Battery Charging)을 수행할 수 있다. 이러한 임시 목표(Temporary Goal)는 주요 작업(Primary Task)을 대체하는 것이 아니라 지원해야 한다. 평가는 장시간 실행 과정에서 발생하는 목표 이탈(Goal Drift), 요구 사항 망각(Forgotten Requirement), 부적절한 우선순위 변경(Inappropriate Priority Change)을 식별해야 한다.

세계 상태 일관성(World State Consistency)은 계획이 현재 환경(Current Environment)에 대한 정확한 표현에 의존하기 때문에 필수적이다. 오래된 물체 위치(Outdated Object Location)나 잘못된 작업 상태(Incorrect Task Status)는 계획기가 더 이상 적절하지 않은 행동을 선택하게 만들 수 있다. 일관되지 않은 상태 추정값(Inconsistent State Estimate)에 기반한 재계획은 추가적인 오류를 유발할 수 있다. 평가는 계획 결정(Planning Decision)이 갱신된 관측(Updated Observation)을 사용하는지, 감지된 모순(Detected Contradiction)이 실행 전에 상태 검증(State Verification)을 유발하는지 검토해야 한다.

시간적 제약 조건(Temporal Constraint)은 장기 계획의 복잡성을 더욱 증가시킨다. 일부 행동은 마감 시간(Deadline) 전에 수행되어야 하며, 다른 행동은 외부 시스템(External System)이나 인간 운영자(Human Operator)와의 동기화(Synchronization)에 의존한다. 계획이 논리적으로 올바르더라도 시간 요구 사항(Timing Requirement)을 위반하면 운영상 실패할 수 있다. 평가는 일정 실행 가능성(Schedule Feasibility), 마감 시간 준수(Deadline Compliance), 대기 시간(Waiting Time), 지연이 발생했을 때 행동 시점(Action Timing)을 수정하는 시스템의 능력을 측정해야 한다.

자원 인식 계획(Resource-Aware Planning)은 에너지(Energy), 연산 용량(Computational Capacity), 적재 하중 제한(Payload Limit), 도구(Tool), 작업 공간 가용성(Workspace Availability)을 고려해야 한다. 로봇은 무거운 물체를 운반하기 전에 충전하거나 제한된 구역(Restricted Area)에 진입하기 전에 장비를 확보해야 할 수 있다. 부적절한 자원 할당(Resource Allocation)은 초기 작업이 성공하더라도 이후 하위 작업을 불가능하게 만들 수 있다. 평가는 계획이 임무 완료에 충분한 자원을 보존하고 자원 가용성(Resource Availability)의 변화에 적절하게 대응하는지 판단해야 한다.

안전 제약 조건(Safety Constraint)은 초기 계획(Initial Planning)과 재계획(Replanning) 모두에서 유효하게 유지되어야 한다. 이동 시간을 단축하는 대체 경로라도 제한 구역(Restricted Zone)을 통과하거나 사람 주변의 이격 거리(Clearance)를 줄인다면 허용되지 않을 수 있다. 마찬가지로 수정된 조작 순서(Revised Manipulation Sequence)는 불안정한 물체 구성(Unstable Object Configuration)을 초래할 수 있다. 평가는 생성된 계획이 필수 안전 요구 사항(Mandatory Safety Requirement)을 충족하고 재계획 과정에서 안전하지 않은 지름길(Unsafe Shortcut)을 허용 가능한 진전으로 취급하지 않는지 검증해야 한다.

계획 효율성(Planning Efficiency)은 연산 노력(Computational Effort)과 선택된 행동의 품질(Action Quality) 사이의 균형을 포함한다. 더 광범위한 탐색(Extensive Search)은 더 나은 계획을 생성할 수 있지만 동적 환경(Dynamic Environment)에서는 허용할 수 없는 지연을 발생시킬 수 있다. 반대로 지나치게 단순화된 계획(Simplified Planning)은 중요한 의존성을 놓칠 수 있다. 평가는 의사결정이 이루어져야 하는 운영상 마감 시간(Operational Deadline)을 고려하면서 계획 지연 시간(Planning Latency), 연산 자원 소비(Computational Consumption), 해의 품질(Solution Quality), 실행 성능(Execution Performance)을 측정해야 한다.

모델 예측 계획(Model Predictive Planning)은 제한된 미래 시간 범위(Future Horizon)에 걸쳐 행동을 반복적으로 최적화함으로써 적응성(Adaptability)을 유지하는 접근 방식 중 하나이다. 시스템은 계획의 일부를 실행하고 새로운 관측을 반영한 다음 후속 의사결정을 갱신한다. 이러한 과정은 대응성(Responsiveness)을 향상할 수 있지만 계획 범위(Planning Horizon)가 충분하지 않으면 먼 미래의 결과(Distant Consequence)를 놓칠 수 있다. 평가는 국소 최적화(Local Optimization)가 장기 임무 목표(Long-Term Mission Objective)와 일치하는지 검토해야 한다.

계획 및 재계획 성능(Planning and Replanning Performance)은 결과 기반 지표(Outcome-Based Metric)와 과정 기반 지표(Process-Based Metric)를 모두 사용하여 평가해야 한다. 최종 임무 성공(Final Mission Success)은 목표 달성 여부를 보여주지만 중간 측정값(Intermediate Measure)은 계획의 약점을 드러낸다. 유용한 지표에는 계획 실행 가능성(Plan Feasibility), 하위 목표 완료(Subgoal Completion), 재계획 지연 시간(Replanning Latency), 수정 빈도(Revision Frequency), 실행 편차(Execution Deviation), 복구 효과(Recovery Effectiveness)가 포함된다. 이러한 측정값은 계획 실패(Planning Failure)를 인식 및 제어의 한계(Perception and Control Limitation)와 구분해야 한다.

벤치마크 시나리오(Benchmark Scenario)는 임무 실행의 서로 다른 단계에서 통제된 외란(Controlled Disturbance)을 도입해야 한다. 내비게이션(Navigation)이 시작된 이후 장애물이 나타나거나 물체를 사용할 수 없게 되거나 자원 제약 조건(Resource Constraint)이 예상하지 못하게 변화할 수 있다. 다양한 임무 길이(Mission Length)와 외란 패턴(Disturbance Pattern)에 걸친 반복 시험(Repeated Trial)은 재계획 역량(Replanning Capability)이 일반화되는지 보여줄 수 있다. 평가는 동등한 조건에서 초기 계획 품질(Initial Plan Quality)과 시스템의 적응 능력(Adaptation Capability)을 비교해야 한다.

반사실적 분석(Counterfactual Analysis)은 대체 계획 결정(Alternative Planning Decision)이 임무 결과(Mission Outcome)를 개선할 수 있었는지 평가하는 데 도움이 된다. 시뮬레이션(Simulation)에서는 평가자가 이전 상태(Earlier State)를 복원하고 통제된 외란 조건에서 서로 다른 계획을 비교할 수 있다. 이러한 접근 방식은 비효율적인 선택(Inefficient Choice)과 핵심 의존성(Critical Dependency)을 드러낼 수 있다. 그러나 결론은 시뮬레이션 충실도(Simulation Fidelity)와 가정된 환경 동역학(Assumed Environmental Dynamics)의 타당성에 의존하므로 실제 물리 시스템(Physical System)에 적용할 때 신중하게 해석해야 한다.

장기 계획(Long-Horizon Planning)은 일관된 실행 이력(Coherent Execution History)을 유지하는 것도 요구한다. 시스템은 완료된 행동(Completed Action), 실패한 시도(Failed Attempt), 수정된 가정(Revised Assumption), 계획 변경 이유(Reason for Plan Change)를 기록해야 한다. 이러한 기록은 디버깅(Debugging)을 지원하고 반복적인 실수를 방지한다. 평가는 로봇이 이전 경험을 고려하지 않고 계획을 반복적으로 재구성하는 대신 과거 정보(Historical Information)를 활용하여 후속 의사결정(Subsequent Decision)을 개선하는지 판단해야 한다.

궁극적으로 장기 계획 및 재계획(Long-Horizon Planning and Replanning)은 피지컬 인공지능(Physical AI) 시스템이 복잡한 목표(Complex Objective)를 지속적이고 적응 가능하며 안전한 물리적 행동(Sustained, Adaptable, and Safe Physical Behavior)으로 전환할 수 있는지 측정한다. 신뢰할 수 있는 자율성(Reliable Autonomy)은 초기 행동 시퀀스(Initial Action Sequence)를 생성하는 것 이상을 요구하며, 불확실성과 변화에 지능적으로 대응하면서 임무 의도(Mission Intent)를 보존해야 한다. 포괄적인 평가(Comprehensive Evaluation)는 계획 역량(Planning Competence)이 현실적인 환경(Realistic Environment)에서 일관된 임무 완료(Consistent Mission Completion)를 지원하는지 보여준다.

## 06.10. Failure Detection and Recovery

![](images/image10.png){width="7.268055555555556in" height="7.268055555555556in"}

![](images/image11.png){width="7.268055555555556in" height="7.268055555555556in"}

실패 감지 및 복구(Failure Detection and Recovery)는 장기 임무(Long-Horizon Mission)가 필연적으로 로봇을 예상하지 못한 조건과 실행 오류(Execution Error)에 노출시키기 때문에 장기 피지컬 인공지능(Physical AI) 시스템을 평가하는 데 필수적인 역량이다. 로봇은 인식 실패(Perception Failure), 내비게이션 장애물(Navigation Obstacle), 조작 오류(Manipulation Error), 변화하는 환경 상태(Environmental State)에 직면할 수 있다. 평가는 시스템이 이러한 실패를 인식하고, 그 결과를 진단하며, 안전성을 저해하지 않으면서 작업 진행을 복원할 수 있는지 판단해야 한다.

실패 감지(Failure Detection)는 예상된 시스템 동작(Expected System Behavior)과 관측된 시스템 동작(Observed System Behavior) 사이의 편차(Deviation)를 식별하는 것을 의미한다. 로봇은 파지(Grasp)를 통해 물체를 안정적으로 잡을 것으로 예측할 수 있지만, 힘 측정값(Force Measurement)이나 시각적 관측(Visual Observation)은 물체가 미끄러졌음을 나타낼 수 있다. 이러한 불일치를 감지하려면 발행된 명령(Issued Command)이 성공적으로 완료되었다고 가정하는 대신 행동 결과(Action Outcome)를 감시해야 한다. 평가는 감지 정확도(Detection Accuracy), 응답 지연 시간(Response Latency), 실제 실패(Genuine Failure)와 센서 잡음(Sensor Noise)을 구분하는 능력을 평가해야 한다.

장기 임무(Long-Horizon Mission)는 여러 추상화 수준(Abstraction Level)에서 실패를 포함한다. 하위 수준 실패(Low-Level Failure)에는 액추에이터 포화(Actuator Saturation), 불안정한 접촉(Unstable Contact), 위치 추정 오류(Localization Error)가 포함되며, 작업 수준 실패(Task-Level Failure)에는 미완료 하위 작업(Incomplete Subtask)이나 위반된 의존 관계(Violated Dependency)가 포함된다. 임무 수준 실패(Mission-Level Failure)는 누적된 지연(Accumulated Delay)이나 자원 부족(Resource Shortage)으로 인해 최종 목표(Final Objective)에 도달할 수 없게 될 때 발생할 수 있다. 평가는 시스템이 적절한 수준에서 실패를 식별하고 후속 행동(Subsequent Action)에 미치는 영향을 이해하는지 판단해야 한다.

실패 감지(Failure Detection)는 정상 작동(Normal Operation)에 대한 신뢰할 수 있는 기대값(Expectation)에 의존한다. 이러한 기대값은 물리 모델(Physics Model), 학습된 예측(Learned Prediction), 작업 명세(Task Specification), 과거 성능(Historical Performance)에서 도출될 수 있다. 감시 시스템(Monitoring System)은 관측된 결과(Observed Outcome)를 예측된 상태(Predicted State) 및 사전에 정의된 제약 조건(Predefined Constraint)과 비교한다. 평가는 시스템이 변화하는 운영 조건(Operating Condition)에서 의미 있는 편차(Meaningful Deviation)를 감지하면서 실행을 불필요하게 중단시키는 과도한 오경보(False Alarm)를 발생시키지 않는지 검토해야 한다.

실패 분류(Failure Classification)는 서로 다른 원인과 결과를 구분함으로써 적절한 복구 결정(Recovery Decision)을 지원한다. 파지 실패(Failed Grasp)는 부정확한 물체 위치 추정(Inaccurate Object Localization), 불충분한 파지력(Insufficient Gripping Force), 예상하지 못한 형상(Unexpected Geometry), 기계적 오작동(Mechanical Malfunction)으로 인해 발생할 수 있다. 이러한 실패는 겉으로 비슷한 결과를 나타낼 수 있지만 서로 다른 대응을 요구한다. 평가는 로봇이 효과가 없는 수정 작업을 반복하는 대신 실제 대응에 활용할 수 있는 실패 범주(Actionable Failure Category)를 식별하는지 평가해야 한다.

시간적 실패 감지(Temporal Failure Detection)는 일부 오류가 여러 행동 이후에야 드러나기 때문에 특히 중요하다. 잘못 배치된 물체(Incorrectly Placed Object)는 이후 조립 작업(Assembly Operation)이 실패할 때까지 발견되지 않을 수 있다. 마찬가지로 작은 위치 추정 오류(Localization Error)는 내비게이션(Navigation)이 불안정해지기 전까지 누적될 수 있다. 평가는 실패 발생(Failure Occurrence)과 감지(Detection) 사이의 지연 시간을 측정해야 하며, 오류가 더 큰 임무 중단(Mission Disruption)으로 전파되기 전에 시스템이 조기 경고 신호(Early Warning Signal)를 식별하는지도 포함해야 한다.

복구(Recovery)는 현재 작업을 안전하게 계속할 수 있는지 판단하는 것에서 시작한다. 로봇은 실패의 심각도(Failure Severity), 세계 상태(World State)의 유효성, 대체 행동(Alternative Action)의 가용성을 평가해야 한다. 경미한 편차(Minor Deviation)는 국소적 수정(Local Correction)으로 해결할 수 있지만 중대한 실패(Significant Failure)는 재계획(Replanning)이나 인간 지원(Human Assistance)을 요구할 수 있다. 평가는 선택된 대응이 실패의 심각도에 적합하고 불필요한 대응 수준 확대(Unnecessary Escalation)나 안전하지 않은 작업 지속(Unsafe Continuation)을 방지하는지 검토해야 한다.

국소 복구 전략(Local Recovery Strategy)은 전체 임무 계획(Overall Mission Plan)을 크게 변경하지 않고 실패를 해결한다. 로봇은 장애물을 만난 후 파지 자세(Grasp Pose)를 조정하거나 인식 측정(Perception Measurement)을 반복하거나 인접한 내비게이션 경유점(Navigation Waypoint)을 선택할 수 있다. 이러한 행동은 제한된 연산 및 운영 비용(Computational and Operational Cost)으로 작업 진행을 복원할 수 있다. 평가는 국소 복구 성공률(Local Recovery Success Rate), 추가 실행 시간(Additional Execution Time), 반복 시도(Repeated Attempt)가 결과를 개선하는지 측정해야 한다.

전역 복구(Global Recovery)는 실패가 임무 계획(Mission Plan)의 주요 가정이나 의존 관계를 무효화할 때 필요해진다. 사용할 수 없는 도구(Unavailable Tool), 접근할 수 없는 목적지(Inaccessible Destination), 고갈된 에너지 비축량(Depleted Energy Reserve)은 여러 하위 작업(Subtask)의 재구성을 요구할 수 있다. 시스템은 완료된 작업(Completed Work)을 보존하면서 영향을 받은 계획 부분만 수정해야 한다. 평가는 전역 복구가 모순된 목표(Contradictory Goal)나 불필요한 반복(Unnecessary Repetition)을 발생시키지 않으면서 실행 가능성(Feasibility)을 복원하는지 평가해야 한다.

복구 정책(Recovery Policy)은 반복 실패(Repeated Failure)의 위험을 고려해야 한다. 근본적인 조건(Underlying Condition)을 변경하지 않고 실패한 행동을 재시도하면 자원을 낭비하거나 물리적 손상(Physical Damage)을 증가시킬 수 있다. 유능한 로봇은 추가 시도(Additional Attempt)가 정당한 시점과 대체 전략(Alternative Strategy)이 더 바람직한 시점을 판단해야 한다. 평가는 재시도 제한(Retry Limit), 전략 다양성(Strategy Diversity), 추가적인 자율 시도(Autonomous Attempt)가 성공할 가능성이 낮은 상황을 인식하는 능력을 검토해야 한다.

세계 상태 검증(World State Verification)은 실패 이후 로봇의 내부 표현(Internal Representation)이 더 이상 물리적 현실(Physical Reality)과 일치하지 않을 수 있기 때문에 중요하다. 떨어뜨린 물체(Dropped Object)는 예측하기 어려운 방향으로 이동했을 수 있으며, 실패한 조작(Failed Manipulation)은 주변 구성 요소(Nearby Component)의 배치를 변경했을 수 있다. 복구는 신뢰할 수 있는 상태 추정값(Trustworthy State Estimate)을 확립하기 위한 충분한 관측(Observation)에서 시작해야 한다. 평가는 후속 행동(Subsequent Action)이 오래된 가정(Outdated Assumption)이 아니라 검증된 조건(Verified Condition)에 의존하는지 판단해야 한다.

안전을 고려한 복구(Safety-Aware Recovery)는 복구 과정 전체에서 운영 제약 조건(Operational Constraint)을 유지해야 한다. 떨어뜨린 물체를 회수하려는 로봇은 원래 작업을 완료하기 위해 위험 구역(Hazardous Area)에 진입하거나 액추에이터 한계(Actuator Limit)를 초과해서는 안 된다. 안전한 복구(Safe Recovery)가 불가능한 경우 시스템은 적절한 최소 위험 상태(Minimum-Risk Condition)로 전환해야 한다. 평가는 임무 완료(Mission Completion)가 일시적으로 또는 영구적으로 불가능해지더라도 복구 행동(Recovery Action)이 안전하게 유지되는지 검증해야 한다.

인간 지원(Human Assistance)은 자율 역량(Autonomous Capability)이 충분하지 않을 때 중요한 복구 수단(Recovery Option)이 된다. 로봇은 모호하거나 위험한 상황을 해결하기 위해 명확화 요청(Clarification Request), 원격 개입(Remote Intervention), 물리적 지원(Physical Assistance)을 요청할 수 있다. 효과적인 대응 수준 확대(Effective Escalation)를 위해서는 실패 내용, 관련 관측(Relevant Observation), 시도한 수정 행동(Attempted Corrective Action)을 전달해야 한다. 평가는 지원 빈도(Assistance Frequency), 대응 수준 확대의 적절성(Escalation Appropriateness), 인간 개입(Human Intervention)이 성공적인 임무 지속(Mission Continuation)에 기여하는 정도를 측정해야 한다.

복구 효과(Recovery Effectiveness)는 초기 작업 성공(Initial Task Success)과 별도로 평가해야 한다. 두 로봇이 유사한 실패율(Failure Rate)을 보이더라도 작업 진행을 복원하는 능력에는 상당한 차이가 있을 수 있다. 초기 신뢰성(Initial Reliability)이 보통 수준인 시스템도 효과적인 복구를 통해 높은 임무 완료율(Mission Completion Rate)을 달성할 수 있지만, 다른 시스템은 사소한 외란(Minor Disturbance) 이후 작업을 종료할 수 있다. 따라서 평가는 실패 발생(Failure Occurrence), 감지 성능(Detection Performance), 복구 성공(Recovery Success), 최종 임무 결과(Final Mission Outcome)를 구분해야 한다.

정량적 지표(Quantitative Metrics)에는 실패 감지 정밀도(Failure Detection Precision), 재현율(Recall), 감지 지연 시간(Detection Latency), 진단 정확도(Diagnosis Accuracy), 복구 성공률(Recovery Success Rate), 평균 복구 시간(Mean Recovery Time)이 포함될 수 있다. 추가적인 측정값은 반복 실패 빈도(Repeated Failure Frequency), 개입률(Intervention Rate), 손실된 작업 진전(Lost Progress), 복구 중 자원 소비(Resource Consumption)를 포착할 수 있다. 이러한 지표는 빠른 복구가 안전성을 희생하거나 신뢰할 수 없는 작업 완료(Unreliable Task Completion)를 초래한다면 반드시 바람직한 것은 아니므로 함께 해석해야 한다.

벤치마크 시나리오(Benchmark Scenario)는 비교 가능한 평가 조건(Comparable Evaluation Condition)을 보장하기 위해 통제된 실패 주입(Controlled Failure Injection)을 포함해야 한다. 예시에는 일시적인 센서 성능 저하(Temporary Sensor Degradation), 차단된 경로(Blocked Route), 잘못 배치된 물체(Misplaced Object), 액추에이터 제한(Actuator Limitation), 통신 중단(Interrupted Communication)이 포함된다. 각 시나리오는 관측 가능한 실패 조건(Observable Failure Condition)과 허용 가능한 복구 결과(Acceptable Recovery Outcome)를 정의해야 한다. 서로 다른 실패 유형(Failure Type)과 임무 단계(Mission Stage)에 걸친 반복 시험(Repeated Trial)은 복구 역량(Recovery Capability)이 익숙한 외란을 넘어 일반화되는지 보여줄 수 있다.

실패 전파 분석(Failure Propagation Analysis)은 국소 오류(Local Error)가 이후 임무 단계(Mission Stage)에 어떤 영향을 미치는지 판단하는 데 도움이 된다. 파지 실패(Missed Grasp)는 운반을 지연시키고 후속 조립 단계(Subsequent Assembly Step)를 무효화하며 결국 임무 완료(Mission Completion)를 방해할 수 있다. 평가는 모든 실패 결과를 마지막으로 관측된 오류(Final Visible Error)에 귀속시키는 대신 이러한 인과 관계(Causal Relationship)를 추적해야 한다. 이러한 접근 방식은 조기 감지(Early Detection)와 표적 복구(Targeted Recovery)가 후속 실패(Downstream Failure)의 누적을 줄이는지 보여준다.

복구 평가(Recovery Evaluation)는 시간적 의존성(Temporal Dependency)과 임무 마감 시간(Mission Deadline)도 고려해야 한다. 로봇이 국소 오류(Local Error)를 성공적으로 수정하더라도 지나치게 많은 시간을 소비하면 전체 임무(Overall Mission)가 실행 불가능해질 수 있다. 마찬가지로 반복적인 복구 시도(Repeated Recovery Attempt)는 배터리 용량(Battery Capacity)이나 연산 자원(Computational Resource)을 고갈시킬 수 있다. 평가는 복구가 남은 작업(Remaining Task)에 충분한 시간과 자원을 보존하는지, 시스템이 작업을 계속하는 것이 더 이상 실용적이지 않은 시점을 인식하는지 측정해야 한다.

실패로부터의 학습(Learning from Failures)은 이전 경험(Previous Experience)이 향후 의사결정(Future Decision)을 지원할 때 장기 자율성(Long-Horizon Autonomy)을 향상할 수 있다. 로봇은 실패한 파지 구성(Unsuccessful Grasp Configuration), 신뢰할 수 없는 경로(Unreliable Route), 반복 오류(Repeated Error)와 관련된 환경 조건(Environmental Condition)을 기록할 수 있다. 이러한 기록은 이후 임무에서 더 나은 계획(Planning)과 복구 선택(Recovery Selection)을 지원할 수 있다. 평가는 축적된 경험(Accumulated Experience)이 익숙하지 않은 상황(Unfamiliar Situation)에서 부적절한 가정(Inappropriate Assumption)을 도입하지 않으면서 반복적인 실패를 줄이는지 검토해야 한다.

포괄적인 실패 평가 프레임워크(Comprehensive Failure Evaluation Framework)는 지속적인 감시(Continuous Monitoring), 실패 진단(Failure Diagnosis), 복구 선택(Recovery Selection), 실행 검증(Execution Verification), 임무 수준 평가(Mission-Level Assessment)를 통합해야 한다. 상세한 로그(Detailed Log)는 예상 상태(Expected State), 관측된 편차(Observed Deviation), 진단 결정(Diagnostic Decision), 수정 행동(Corrective Action), 최종 결과(Final Outcome)를 보존해야 한다. 궁극적으로 실패 감지 및 복구(Failure Detection and Recovery)는 외란(Disturbance), 불확실성(Uncertainty), 불완전한 실행(Imperfect Execution)에도 불구하고 피지컬 인공지능(Physical AI) 시스템이 신뢰할 수 있는 자율성(Dependable Autonomy)을 지속할 수 있는지 결정한다.

## 06.11. Intervention and Human Assistance Rate

![](images/image12.png){width="7.268055555555556in" height="7.268055555555556in"}

개입률 및 인간 지원률(Intervention and Human Assistance Rate)은 임무 완료(Mission Completion)만으로는 로봇이 얼마나 독립적으로 작동하는지 알 수 없기 때문에 장기 피지컬 인공지능(Long-Horizon Physical AI)의 자율성을 평가하는 핵심 지표이다. 시스템은 빈번한 운영자 수정(Operator Correction)이나 원격 제어(Remote Control)에 의존하면서도 복잡한 작업을 성공적으로 완료할 수 있다. 평가는 인간 참여(Human Involvement)의 빈도, 지속 시간, 목적을 정량화하여 진정한 자율 역량(Genuine Autonomous Capability)과 인간 지원 실행(Human-Supported Execution)을 구분해야 한다.

개입(Intervention)은 작업 실행 중 외부 행위자(External Agent)가 로봇의 자율 행동(Autonomous Behavior)을 수정하거나 중단하거나 무시하고 다른 행동으로 대체하는 경우를 의미한다. 예시에는 비상 정지(Emergency Stop), 수동 내비게이션 수정(Manual Navigation Correction), 원격 조작(Teleoperation), 작업 계획(Task Plan)의 직접적인 변경이 포함된다. 인간 지원(Human Assistance)은 더 넓은 개념으로, 정보 제공(Information Provision), 지시 명확화(Instruction Clarification), 물리적 환경 준비(Physical Environment Preparation)를 포함할 수 있다. 평가 절차(Evaluation Protocol)는 일관되지 않은 보고를 방지하기 위해 이러한 범주를 명시적으로 정의해야 한다.

개입률(Intervention Rate)은 정의된 운영 노출량(Exposure)이나 작업량(Workload)에 비해 외부 수정 행동(External Corrective Action)이 얼마나 자주 발생하는지 측정한다. 이는 운영 시간당 개입 횟수(Interventions per Operating Hour), 완료된 작업당 개입 횟수(Interventions per Completed Task), 임무당 개입 횟수(Interventions per Mission), 이동 거리당 개입 횟수(Interventions per Distance Traveled)로 표현할 수 있다. 이러한 분모(Denominator)는 자율성의 서로 다른 측면을 나타내므로 상호 교환 가능한 것으로 취급해서는 안 된다. 평가는 선택한 정규화 기준(Normalization Basis)을 보고하고 임무 복잡도(Mission Complexity)와 운영 조건(Operating Condition)이 해석에 미치는 영향을 설명해야 한다.

인간 지원률(Human Assistance Rate)은 로봇이 할당된 작업을 계속하거나 완료하기 위해 인간의 지원을 필요로 하는 빈도를 측정한다. 지원에는 질문에 대한 답변, 불확실한 관측(Uncertain Observation)의 확인, 물체 위치 재조정(Object Repositioning), 예상하지 못한 환경 조건(Environmental Condition)의 해결이 포함될 수 있다. 직접 개입(Direct Intervention)과 달리 인간 지원이 항상 로봇으로부터 제어권(Control Authority)을 이전하는 것은 아니다. 평가는 정보적 지원(Informational Support), 물리적 지원(Physical Assistance), 제어권 인수(Control Takeover)를 구분해야 한다.

개입 심각도(Intervention Severity)는 모든 개입 사건이 동일한 운영상 결과(Operational Consequence)를 갖는 것은 아니기 때문에 중요하다. 짧은 지시 명확화(Instruction Clarification)는 장시간의 원격 조작(Teleoperation Session)이나 비상 종료(Emergency Shutdown)와 상당한 차이가 있다. 평가는 긴급성(Urgency), 지속 시간(Duration), 필요한 전문성(Required Expertise), 임무 연속성(Mission Continuity)에 미치는 영향에 따라 사건을 분류해야 한다. 심각도 가중 보고(Severity-Weighted Reporting)는 단순 사건 횟수(Raw Event Count)를 보완할 수 있지만, 가중치 규칙(Weighting Rule)은 명확하게 정의되고 정당화되어야 한다.

장기 평가(Long-Horizon Evaluation)는 개입의 시간적 분포(Temporal Distribution)를 고려해야 한다. 한 로봇은 수 시간 동안 독립적으로 작동한 후 지원을 요청할 수 있지만, 다른 로봇은 일정한 간격으로 작은 수정 작업을 요청할 수 있다. 따라서 동일한 평균 개입률(Average Intervention Rate)이 서로 다른 자율성 패턴(Autonomy Pattern)을 감출 수 있다. 평가는 개입 시점(Intervention Timing), 개입 집중 현상(Intervention Clustering), 지원 사건(Assistance Event)과 특정 임무 단계(Mission Stage) 사이의 관계를 검토해야 한다.

요청된 지원(Requested Assistance)과 외부에서 강제로 수행된 개입(Externally Imposed Intervention)을 구분하는 것은 특히 중요하다. 로봇이 불확실성(Uncertainty)이 허용 가능한 임계값(Acceptable Threshold)을 초과할 때 선제적으로 명확화를 요청하는 것은 적절한 자기 감시(Self-Monitoring) 능력을 보여줄 수 있다. 반대로 로봇이 위험한 조건(Dangerous Condition)을 인식하지 못해 운영자가 개입할 수도 있다. 평가는 모든 지원 요청을 낮은 자율성(Poor Autonomy)의 증거로 가정하지 않고 이러한 경우를 구분해야 한다.

적절한 지원 요청(Appropriate Assistance Seeking)은 안전성(Safety)과 신뢰성(Reliability)을 향상할 수 있다. 자신의 인식(Perception)이나 조작 역량(Manipulation Capability)의 한계를 인식하는 로봇은 오류가 손상을 일으키기 전에 도움을 요청할 수 있다. 그러나 과도한 지원 요청(Excessive Assistance Request)은 확장성(Scalability)을 저해하고 운영 비용(Operational Cost)을 증가시킬 수 있다. 평가는 가능한 한 낮은 지원 요청 빈도만을 보상하는 대신 요청이 불확실성, 작업 난이도(Task Difficulty), 안전 제약 조건(Safety Constraint)에 의해 정당화되는지 판단해야 한다.

허위 자율성(False Autonomy)은 평가 절차(Evaluation Procedure)가 상당한 인간 기여(Human Contribution)를 제외할 때 발생할 수 있다. 운영자는 실패한 시험(Failed Trial)을 초기화하거나 물체를 배치하거나 유리한 시작 조건(Favorable Starting Condition)을 선택하거나 계획을 수정하면서도 이러한 행동이 개입으로 집계되지 않을 수 있다. 이러한 숨겨진 지원(Hidden Assistance)은 보고된 성공률(Reported Success Rate)을 부풀리고 시스템 간 비교를 왜곡할 수 있다. 평가는 준비 활동(Preparation Activity)과 복구 활동(Recovery Activity)을 포함하여 실행에 실질적인 영향을 미치는 모든 인간 기여를 문서화해야 한다.

개입 기록(Intervention Logging)은 각 사건을 둘러싼 상황을 포착해야 한다. 관련 정보에는 타임스탬프(Timestamp), 임무 단계(Mission Phase), 유발 조건(Triggering Condition), 지원 유형(Assistance Type), 지속 시간(Duration), 운영자 식별 정보 또는 역할(Operator Identity or Role), 결과적인 작업 상태(Resulting Task Status)가 포함된다. 로그(Log)는 제어권 이전(Control Transfer) 여부, 자율 실행(Autonomous Execution)의 재개 여부, 원래 목표(Original Objective)의 달성 가능성 유지 여부도 기록해야 한다. 일관된 사건 기록(Consistent Event Record)은 재현 가능한 분석(Reproducible Analysis)과 감사(Auditing)를 지원한다.

인간 지원 시간(Human Assistance Duration)은 개입 빈도(Intervention Frequency)만으로 파악할 수 없는 정보를 제공한다. 한 번의 장시간 제어권 인수(Prolonged Takeover)는 여러 차례의 짧은 확인(Brief Confirmation)보다 더 큰 운영 비용을 발생시킬 수 있다. 평가는 총 지원 시간(Total Assisted Time), 평균 지원 지속 시간(Average Assistance Duration), 자율 제어(Autonomous Control) 상태에서 소비한 임무 시간의 비율(Proportion of Mission Time)을 측정해야 한다. 이러한 측정값은 지속적인 감독(Continuous Supervision)이나 운영자의 적극적인 참여(Active Operator Involvement)가 얼마나 필요한지 파악하는 데 도움이 된다.

개입 지표(Intervention Metrics)는 작업 성공(Task Success) 및 실행 품질(Execution Quality)과 함께 해석해야 한다. 빈번한 지원을 통해 모든 임무를 완료하는 로봇은 운영상 유용할 수 있지만, 동일한 임무를 독립적으로 완료하는 로봇과 같은 자율성 평가(Autonomy Assessment)를 받아서는 안 된다. 반대로 도움 요청을 피하면서 반복적으로 실패하는 시스템이 더 우수하다고 평가되어서도 안 된다. 평가는 자율성(Autonomy), 신뢰성(Reliability), 전반적인 유용성(Overall Utility) 사이의 차이를 유지해야 한다.

작업 난이도(Task Difficulty)는 개입 빈도(Intervention Frequency)에 큰 영향을 미친다. 구조화된 환경(Structured Environment)에서 반복적인 작업은 지원이 거의 필요하지 않을 수 있지만, 익숙하지 않은 물체(Unfamiliar Object), 혼잡한 공간(Crowded Space), 변화하는 조건(Changing Condition)은 추가적인 불확실성을 발생시킨다. 공정한 비교(Fair Comparison)를 위해서는 임무 지속 시간(Mission Duration), 작업 복잡도(Task Complexity), 환경 변동성(Environmental Variability), 운영 설계 영역(Operational Design Domain)을 통제해야 한다. 이러한 조건 없이 개입률을 보고하면 시스템 역량(System Capability)에 대한 잘못된 결론을 도출할 수 있다.

운영자 행동(Operator Behavior)은 벤치마크 결과(Benchmark Result)에 추가적인 변동성(Variability)을 도입할 수 있다. 숙련된 운영자(Experienced Operator)는 경험이 부족한 인력보다 더 일찍 개입하거나 문제를 더 빠르게 해결할 수 있다. 조직마다 수동 제어권 인수(Manual Takeover)에 적용하는 임계값(Threshold)도 다를 수 있다. 평가 절차(Evaluation Protocol)는 개입 기준(Intervention Criteria), 운영자 교육(Operator Training), 허용 가능한 지원(Permissible Assistance)을 표준화해야 한다. 완전한 표준화(Complete Standardization)가 불가능한 경우 운영자 관련 변동성(Operator-Related Variability)을 문서화하고 분석해야 한다.

시간에 따른 자율성 저하(Autonomy Degradation over Time)는 개입 빈도(Intervention Frequency)의 변화를 통해 감지할 수 있다. 로봇은 초기에는 안정적으로 작동하지만 위치 추정 드리프트(Localization Drift), 기억 오류(Memory Error), 자원 제약(Resource Constraint)이 누적되면서 점점 더 많은 지원을 필요로 할 수 있다. 평가는 전체 집계값(Aggregate Total)에만 의존하지 않고 연속적인 임무 구간(Successive Mission Interval)에 걸쳐 개입률을 측정해야 한다. 이러한 분석은 단기 시험(Short-Duration Test)에서 발견하기 어려운 점진적인 성능 저하(Progressive Deterioration)를 드러낼 수 있다.

개입 효율성(Intervention Efficiency)은 인간 참여(Human Involvement)가 임무 진행(Mission Progress)에 의미 있는 개선을 가져오는지 검토한다. 중요한 장애물을 해결하여 이후 수 시간의 자율 운영(Autonomous Operation)을 가능하게 하는 지원은 동일한 미해결 문제(Unresolved Problem)를 반복적으로 수정하는 것보다 더 가치가 있을 수 있다. 평가는 각 개입으로 복원된 작업 진전(Restored Progress), 예방된 실패(Prevented Failure), 가능해진 자율 운영을 평가해야 한다. 이를 통해 지원 요구 사항(Assistance Requirement)을 실제 임무 결과(Practical Mission Outcome)와 연결할 수 있다.

인간 지원(Human Assistance)은 작업 부담(Workload)과 확장성(Scalability)에 관한 문제도 발생시킨다. 개별 로봇이 높은 작업 성공률(Task Success Rate)을 달성하더라도 지속적인 운영자 주의(Continuous Operator Attention)가 필요한 배치는 대규모 로봇 군집(Robot Fleet)으로 확장하기 어려울 수 있다. 평가는 로봇당 운영자 투입 시간(Operator Time per Robot), 동시 감독 용량(Simultaneous Supervision Capacity), 긴급 지원 요청(Urgent Assistance Request)의 빈도를 추정해야 한다. 이러한 측정값은 자율성 성능(Autonomy Performance)이 지속 가능한 운영 배치(Sustainable Operational Deployment)를 지원하는지 판단하는 데 도움이 된다.

벤치마크 설계(Benchmark Design)는 현실적인 개입 가능성(Realistic Intervention Opportunity)을 발생시키는 시나리오를 포함해야 한다. 예시에는 모호한 지시(Ambiguous Instruction), 차단된 통로(Blocked Passage), 잘못 배치된 물체(Misplaced Object), 불확실한 조작 결과(Uncertain Manipulation Outcome), 일시적인 센서 고장(Temporary Sensor Failure)이 포함된다. 각 시나리오는 자율 복구(Autonomous Recovery)가 기대되는 시점과 인간 지원이 허용되는 시점을 정의해야 한다. 평가는 정당한 대응 수준 확대(Justified Escalation)를 성급한 지원 요청(Premature Request) 및 안전하지 않은 작업 지속(Unsafe Persistence)과 구분해야 한다.

통계적 보고(Statistical Reporting)에는 개입 횟수(Intervention Count), 노출량 정규화 개입률(Exposure-Normalized Rate), 불확실성 추정값(Uncertainty Estimate), 반복 시험(Repeated Trial)에 걸친 분포(Distribution)가 포함되어야 한다. 드물지만 심각한 개입(Rare but Severe Intervention)은 일상적인 지원 사건(Routine Assistance Event)보다 긴 관측 기간(Observation Period)이 필요할 수 있다. 비교에서는 사건 빈도(Event Frequency)와 임무 간 변동성(Between-Mission Variability)을 모두 고려해야 한다. 신뢰 구간(Confidence Interval)과 명확하게 정의된 집계 규칙(Counting Rule)은 보고된 자율성 성능의 해석 가능성(Interpretability)과 재현성(Reproducibility)을 향상한다.

궁극적으로 개입률 및 인간 지원률(Intervention and Human Assistance Rate)은 장기 피지컬 인공지능(Long-Horizon Physical AI) 시스템의 운영상 독립성(Operational Independence)을 보여준다. 의미 있는 평가(Meaningful Evaluation)를 위해서는 인간이 얼마나 자주 관여하는지뿐 아니라 지원이 필요한 이유, 필요한 노력의 정도, 로봇이 자율 실행(Autonomous Execution)을 성공적으로 재개하는지도 측정해야 한다. 이러한 지표는 기술적 자율성(Technical Autonomy)을 안전성(Safety), 신뢰성(Reliability), 감독 부담(Supervision Burden), 실제 배치 확장성(Real-World Deployment Scalability)과 연결한다.

## 06.12. Autonomy Duration and Mean Time Between Interventions

![](images/image13.png){width="7.268055555555556in" height="7.268055555555556in"}

자율 운영 지속 시간(Autonomy Duration)은 피지컬 인공지능(Physical AI) 시스템이 장기 임무(Extended Mission) 수행 중 외부 개입(External Intervention) 없이 얼마나 오랫동안 작동할 수 있는지를 측정한다. 최종 결과에 초점을 맞추는 작업 성공률(Task Success Rate)과 달리 자율 운영 지속 시간은 독립적인 운영의 연속성(Continuity of Independent Operation)을 나타낸다. 평가는 로봇이 인간 지원(Human Assistance) 없이 변화하는 조건에 대응하면서 인식(Perception), 계획(Planning), 제어(Control), 의사결정(Decision-Making)을 지속적으로 유지할 수 있는지 판단해야 한다.

평균 개입 간 시간(Mean Time Between Interventions, MTBI)은 연속적인 개입 사이의 평균 자율 운영 시간(Average Autonomous Operating Time)을 측정한다. 이는 로봇이 외부 지원(External Assistance)이나 수정 제어(Corrective Control)를 얼마나 자주 필요로 하는지를 나타내는 운영 지표(Operational Indicator)이다. 일반적으로 동일한 조건에서 MTBI가 길수록 독립성(Independence)이 높다는 것을 의미한다. 그러나 시스템 간 차이를 해석하기 전에 개입 정의(Intervention Definition), 임무 복잡도(Mission Complexity), 운영 노출 시간(Exposure Time)을 고려해야 한다.

자율 운영 지속 시간(Autonomy Duration)과 평균 개입 간 시간(MTBI)은 서로 관련되어 있지만 구별되는 특성을 설명한다. 자율 운영 지속 시간은 가장 긴 연속 운영 구간(Longest Uninterrupted Operating Interval), 평균 자율 운영 구간(Average Autonomous Episode), 최초 개입까지의 시간(Time to First Intervention)을 의미할 수 있다. MTBI는 정의된 관측 기간(Observation Period) 동안 개입 사건(Intervention Event) 사이의 시간 간격을 요약한다. 서로 다른 계산 방법(Calculation Method)은 상당히 다른 결과를 생성할 수 있으므로 평가 절차(Evaluation Protocol)는 이러한 정의를 명시해야 한다.

기본적인 MTBI 추정값(MTBI Estimate)은 명확하게 정의된 집계 규칙(Counting Convention)에 따라 누적 자율 운영 시간(Accumulated Autonomous Operating Time)을 집계 대상 개입 횟수(Number of Qualifying Interventions)로 나누어 계산한다. 예를 들어 로봇이 총 20시간의 자율 운영 시간 동안 네 번의 개입을 경험했다면 개입당 5시간이라는 추정값을 얻는다. 이러한 노출 시간 기반 추정값(Exposure-Based Estimate)은 불완전한 구간(Incomplete Interval)을 제외하고 계산한 관측 구간의 산술평균(Arithmetic Mean)과 혼동해서는 안 된다.

측정 경계(Measurement Boundary)는 재현 가능한 평가(Reproducible Evaluation)를 위해 필수적이다. 자율 운영 구간(Autonomous Interval)은 로봇이 제어권(Control Authority)을 확보할 때 시작하여 인간이 개입하거나 안전 시스템(Safety System)이 제어를 무시하고 개입하거나 임무가 종료될 때 끝날 수 있다. 정기 유지보수(Scheduled Maintenance), 충전(Charging), 통신 중단(Communication Interruption), 자발적 일시 정지(Voluntary Pause)는 명시적인 처리 기준이 필요하다. 평가는 어떤 사건이 자율 운영을 종료시키고 어떤 기간이 측정된 운영 시간에 포함되는지 문서화해야 한다.

개입(Intervention)은 발생 원인과 운영상 중요도(Operational Significance)에 따라 분류해야 한다. 수동 내비게이션 수정(Manual Navigation Correction), 원격 조작 세션(Teleoperation Session), 비상 정지(Emergency Stop), 작업 수준 지원(Task-Level Assistance)은 서로 다른 수준의 자율성 상실(Loss of Autonomy)을 나타낼 수 있다. 짧은 정보 확인(Informational Clarification)은 물리적 제어(Physical Control)를 중단하지 않더라도 외부 지식(External Knowledge)에 대한 의존성을 나타낼 수 있다. 평가는 이러한 사건 범주(Event Category)를 통합 MTBI 측정값(Aggregate MTBI Measurement)으로 결합하기 전에 개별적으로 보고해야 한다.

장시간 자율 운영(Long-Duration Autonomy)은 상호 연결된 하위 시스템(Interconnected Subsystem) 전반에서 신뢰할 수 있는 성능을 유지하는 데 의존한다. 인식 오류(Perception Error), 위치 추정 드리프트(Localization Drift), 기억 성능 저하(Memory Degradation), 계획 불일치(Planning Inconsistency), 액추에이터 제한(Actuator Limitation)은 점진적으로 누적될 수 있다. 단기 시험(Short Test)에서 우수한 성능을 보이는 로봇도 장시간 운영 중에는 개입 의존성(Intervention Dependence)이 증가할 수 있다. 평가는 운영 노출 시간(Operational Exposure)이 증가함에 따라 자율 운영 지속 시간이 어떻게 변화하는지 검토해야 한다.

중단 없는 자율 운영 구간(Uninterrupted Autonomous Interval)의 분포(Distribution)는 평균값만으로 얻을 수 있는 정보보다 더 많은 정보를 제공하는 경우가 많다. 두 로봇이 동일한 MTBI 값을 나타내더라도 한 로봇은 빈번한 짧은 중단(Short Interruption)과 간헐적인 장시간 운영(Long Run)을 경험할 수 있다. 중앙값 구간 지속 시간(Median Interval Duration), 하위 백분위 성능(Lower-Percentile Performance), 구간 변동성(Interval Variability)은 이러한 차이를 드러내는 데 도움이 된다. 평가는 불안정한 자율 행동(Unstable Autonomy Behavior)을 감추는 단일 평균값(Single Average)에만 의존해서는 안 된다.

최초 개입까지의 시간(Time-to-First-Intervention)은 초기의 중단 없는 자율 운영 기간(Initial Uninterrupted Autonomous Period)을 나타내므로 유용한 보완 지표(Complementary Measure)이다. 이 지표는 로봇이 외부 지원(External Support)을 필요로 하는 조건에 얼마나 빠르게 직면하는지 보여줄 수 있다. 그러나 이후 복구(Subsequent Recovery)나 지속적인 운영(Continued Operation)을 설명하지는 못한다. 따라서 평가는 최초 개입 시점(First-Intervention Timing)을 반복 사건 분석(Repeated-Event Analysis) 및 전체 임무 성능(Total Mission Performance)과 결합해야 한다.

생존 분석(Survival Analysis)은 관측 기간(Observation Period)이 서로 다른 경우 자율 운영 지속 시간을 평가하기 위한 통계적 프레임워크(Statistical Framework)를 제공한다. 개입은 사건(Event)으로 처리할 수 있으며, 개입 없이 종료된 임무는 우측 검열 관측값(Right-Censored Observation)으로 반영할 수 있다. 생존 곡선(Survival Curve)은 운영 시간이 증가함에 따라 개입 없이 유지될 확률(Probability of Remaining Intervention-Free)을 추정한다. 이러한 접근 방식은 성공적으로 종료된 관측을 실패로 잘못 처리하지 않으면서 시스템을 비교하는 데 도움이 된다.

개입 사건(Intervention Event)은 임무 전체에서 일정한 비율(Constant Rate)로 발생하지 않을 수 있다. 초기 운영(Early Operation)에서는 보정 문제(Calibration Difficulty)가 발생할 수 있지만, 후반 단계(Later Stage)에서는 누적된 상태 추정 오류(State-Estimation Error)나 자원 부족(Resource Shortage)이 드러날 수 있다. 평가는 시간 의존적 개입 강도(Time-Dependent Intervention Intensity)를 검토하고 연속적인 운영 구간(Successive Operating Interval)을 비교해야 한다. 자율 운영 지속 시간의 감소는 전체 MTBI가 허용 가능한 수준을 유지하더라도 점진적인 성능 저하(Progressive Degradation)를 나타낼 수 있다.

시스템 간 자율 운영 지속 시간을 비교할 때는 임무 난이도(Mission Difficulty)를 고려해야 한다. 구조화된 창고 내비게이션(Structured Warehouse Navigation), 동적인 건설 환경(Dynamic Construction Environment), 사람이 활동하는 시설(Human-Populated Facility)은 서로 다른 수준의 불확실성(Uncertainty)과 운영 위험(Operational Risk)을 제공한다. 쉬운 환경에서 더 오래 중단 없이 운영했다고 해서 반드시 더 높은 역량(Capability)을 입증하는 것은 아니다. 공정한 벤치마킹(Fair Benchmarking)을 위해서는 비교 가능한 작업(Task), 환경 조건(Environmental Condition), 개입 정책(Intervention Policy)이 필요하다.

자율 운영 지속 시간(Autonomy Duration)은 작업 생산성(Task Productivity) 및 완료 품질(Completion Quality)과 함께 해석해야 한다. 로봇은 유용한 진전(Useful Progress)을 거의 이루지 못하거나 비효율적인 행동(Ineffective Action)을 반복하거나 어려운 작업(Difficult Task)을 회피하면서도 여러 시간 동안 독립적으로 작동할 수 있다. 이러한 행동은 개입이 드물다는 이유만으로 높은 자율성 평가(Autonomy Assessment)를 받아서는 안 된다. 평가는 자율 운영 시간(Autonomous Operating Time)을 검증된 작업 진전(Verified Task Progress), 임무 성공(Mission Success), 실행 효율성(Execution Efficiency)과 연결해야 한다.

안전 고려 사항(Safety Consideration)은 MTBI를 극대화하는 데 중요한 한계를 설정한다. 필요한 지원(Necessary Assistance)을 거부하거나 위험한 조건(Hazardous Condition)에서도 운영을 계속하는 로봇은 실제보다 길게 나타나는 개입 없는 운영 구간(Intervention-Free Interval)을 달성할 수 있다. 적절한 대응 수준 확대(Appropriate Escalation)는 취약성이 아니라 책임 있는 자율성(Responsible Autonomy)을 보여줄 수 있다. 평가는 안전 제약 조건(Safety Constraint)이 충족되고 지원 결정(Assistance Decision)이 정당화되는 경우에만 지속적인 독립 운영(Sustained Independent Operation)을 긍정적으로 평가해야 한다.

인간 개입 지속 시간(Human Intervention Duration)은 운영상 독립성(Operational Independence)의 또 다른 측면을 제공한다. 두 시스템이 유사한 MTBI 값을 갖더라도 각 개입에서 요구하는 운영자 투입 시간(Operator Time)은 상당히 다를 수 있다. 한 시스템은 짧은 확인(Brief Confirmation) 이후 복구될 수 있지만, 다른 시스템은 장시간의 원격 조작(Prolonged Teleoperation)을 필요로 할 수 있다. 평가는 MTBI를 평균 개입 지속 시간(Mean Intervention Duration), 지원 시간 비율(Assisted-Time Fraction), 자율적으로 수행된 운영 비율(Proportion of Autonomous Operation)과 결합해야 한다.

복구 행동(Recovery Behavior)은 개입 빈도(Intervention Frequency)와 임무 연속성(Mission Continuity) 사이의 관계에 큰 영향을 미친다. 실패를 감지하고 효과적인 자율 복구(Autonomous Recovery)를 실행하는 로봇은 중단 없는 운영 기간(Uninterrupted Operating Period)을 연장할 수 있다. 반대로 반복적으로 실패하는 복구 시도(Unsuccessful Recovery Attempt)는 필요한 개입을 지연시키고 위험을 증가시킬 수 있다. 평가는 성공적인 자체 복구(Successful Self-Recovery)와 해결되지 않은 실패(Unresolved Failure)를 단순히 지연시키는 개입 회피(Intervention Avoidance)를 구분해야 한다.

벤치마크 절차(Benchmark Protocol)는 지연되어 나타나는 실패(Delayed Failure)와 변화하는 운영 조건(Changing Operating Condition)을 드러낼 수 있도록 충분한 지속 시간의 임무를 포함해야 한다. 반복 시험(Repeated Trial)에서는 임무 길이(Mission Length), 작업 의존성(Task Dependency), 환경 외란(Environmental Disturbance), 자원 제약 조건(Resource Constraint)을 다양하게 설정해야 한다. 가능하면 개입 타임스탬프(Intervention Timestamp)와 자율 제어 전환(Autonomous Control Transition)을 자동으로 기록해야 한다. 표준화된 기록(Standardized Logging)은 플랫폼 간 일관된 계산과 비교를 지원한다.

통계적 불확실성(Statistical Uncertainty)은 개입이 드물게 발생할 때 특히 중요해진다. 지원 없이 여러 차례의 짧은 시험을 완료한 시스템이라고 해서 MTBI가 매우 높다고 자동으로 가정할 수는 없다. 더 긴 관측 기간(Longer Observation Period)과 반복 임무(Repeated Mission)는 지속적인 자율성(Sustained Autonomy)에 관한 더 강한 증거를 제공한다. 평가는 추정된 성능(Estimated Performance)과 함께 총 운영 노출량(Total Exposure), 개입 횟수(Intervention Count), 신뢰 구간(Confidence Interval), 검열 관측값(Censored Observation)을 보고해야 한다.

군집 수준 평가(Fleet-Level Evaluation)는 자율 운영 지속 시간 분석을 동시에 작동하는 여러 로봇으로 확장한다. 개별 로봇의 MTBI 값이 길더라도 전체 로봇 군집(Robot Fleet)에서는 빈번한 지원 요청(Assistance Request)이 발생할 수 있다. 운영자 작업 부담(Operator Workload)은 개입 도착 패턴(Intervention Arrival Pattern), 사건 지속 시간(Event Duration), 동시 지원 요구(Simultaneous Assistance Demand)에 따라 달라진다. 평가는 개별 로봇의 자율성 향상(Individual Autonomy Improvement)이 확장 가능한 감독 역량(Scalable Supervision Capacity)으로 이어지는지 검토해야 한다.

궁극적으로 자율 운영 지속 시간(Autonomy Duration)과 평균 개입 간 시간(Mean Time Between Interventions, MTBI)은 기술적 성능(Technical Performance)을 지속적인 운영상 독립성(Sustained Operational Independence)과 연결한다. 포괄적인 평가(Comprehensive Evaluation)는 중단 없는 실행(Uninterrupted Execution), 개입 빈도(Intervention Frequency), 안전성(Safety), 생산성(Productivity), 통계적 불확실성(Statistical Uncertainty), 임무 난이도(Mission Difficulty)를 함께 고려해야 한다. 이러한 지표는 피지컬 인공지능(Physical AI) 시스템이 개별 작업(Isolated Task)에서 단순히 성공하는 수준을 넘어 장시간에 걸쳐 신뢰할 수 있는 자율 행동(Dependable Autonomous Behavior)을 유지할 수 있는지 보여준다.

## 06.13. Continuous Operation and Mission Reliability

![](images/image14.png){width="7.268055555555556in" height="7.268055555555556in"}

연속 운영(Continuous Operation)은 실제 임무(Real-World Mission)가 개별 작업 실행(Isolated Task Execution)의 범위를 넘어 장시간 지속되는 경우가 많기 때문에 장기 피지컬 인공지능(Long-Horizon Physical AI)의 기본적인 요구 사항이다. 로봇은 변화하는 환경(Changing Environment)과 운영 요구 사항(Operational Demand)을 관리하면서 인식(Perception), 계획(Planning), 제어(Control), 통신(Communication)을 유지해야 한다. 평가는 시스템이 허용할 수 없는 성능 저하(Unacceptable Degradation), 반복적인 중단(Repeated Interruption), 임무 목표 상실(Loss of Mission Objective) 없이 장시간 유용한 자율 행동(Useful Autonomous Behavior)을 지속할 수 있는지 판단해야 한다.

임무 신뢰성(Mission Reliability)은 피지컬 인공지능(Physical AI) 시스템이 지정된 운영 조건(Operating Condition)과 시간 제약(Time Constraint) 내에서 할당된 목표를 완료할 확률을 의미한다. 개별 행동 성공(Individual Action Success)과 달리 임무 신뢰성은 서로 의존하는 여러 작업(Dependent Operation)의 복합적인 영향을 반영한다. 로봇은 대부분의 하위 작업(Subtask)을 올바르게 수행하더라도 하나의 치명적인 오류(Critical Error)로 인해 전체 임무에 실패할 수 있다. 따라서 평가는 개별 구성 요소 성능(Component Performance)이 아니라 완전한 임무 결과(Complete Mission Outcome)를 고려해야 한다.

연속 운영(Continuous Operation)과 임무 신뢰성(Mission Reliability)은 밀접하게 관련되어 있지만 서로 다른 성능 차원(Performance Dimension)을 나타낸다. 로봇은 의미 있는 작업을 완료하지 못한 채 여러 시간 동안 작동할 수 있으며, 다른 로봇은 임무를 성공적으로 완료하지만 빈번한 재시작(Restart)을 필요로 할 수 있다. 평가는 시스템 가동 시간(System Uptime), 자율 운영 연속성(Autonomous Operating Continuity), 생산적인 실행 시간(Productive Execution Time), 검증된 임무 완료(Verified Mission Completion)를 구분하여 가용성(Availability)을 실제 임무 효과(Mission Effectiveness)와 혼동하지 않도록 해야 한다.

장시간 운영(Long-Duration Operation)은 단기 평가(Short Evaluation)에서 드러나지 않을 수 있는 누적 오류(Accumulating Error)에 시스템을 노출시킨다. 위치 추정 드리프트(Localization Drift), 보정 변화(Calibration Change), 기억 불일치(Memory Inconsistency), 열적 영향(Thermal Effect), 자원 고갈(Resource Depletion)은 점진적으로 성능을 저하시킬 수 있다. 이러한 문제는 인식(Perception), 계획(Planning), 제어(Control) 하위 시스템(Subsystem) 전반에서 상호작용할 수 있다. 평가는 운영 시간이 증가함에 따라 성능이 안정적으로 유지되는지, 임무 실패(Mission Failure)가 발생하기 전에 초기 성능 저하(Emerging Degradation)를 감지하는지 검토해야 한다.

신뢰성(Reliability)은 하드웨어(Hardware), 소프트웨어(Software), 환경 조건(Environmental Condition) 사이의 상호작용에 의존한다. 센서(Sensor)는 간헐적인 고장(Intermittent Failure)을 경험할 수 있고, 액추에이터(Actuator)는 과열될 수 있으며, 통신 채널(Communication Channel)은 불안정해질 수 있다. 소프트웨어 구성 요소(Software Component)는 메모리 누수(Memory Leak), 스케줄링 지연(Scheduling Delay), 내부 상태 불일치(Inconsistent Internal State)를 경험할 수 있다. 평가는 하위 시스템 외란(Subsystem Disturbance)이 전체 임무 실행에 미치는 영향과 시스템 아키텍처(System Architecture)가 국소적인 결함(Localized Fault)의 확대를 방지하는지 식별해야 한다.

운영 가용성(Operational Availability)은 시스템이 의도된 기능(Intended Function)을 수행할 수 있는 상태로 유지되는 시간의 비율을 측정한다. 일반적으로 고장 빈도(Failure Frequency)와 복구 시간(Restoration Time)에 관련되지만, 가용성만으로 자율 역량(Autonomous Competence)이 입증되는 것은 아니다. 로봇은 기술적으로 사용 가능한 상태이면서도 지시를 기다리거나 비효율적인 행동(Ineffective Action)을 수행할 수 있다. 평가는 가용성을 작업 생산성(Task Productivity), 개입 요구 사항(Intervention Requirement), 임무 성공(Mission Success)과 함께 보고해야 한다.

임무 성공 확률(Mission Success Probability)은 명확하게 정의된 조건에서 반복 시험(Repeated Trial)을 통해 추정해야 한다. 각 시험은 임무 목표(Mission Objective), 초기 상태(Starting State), 허용 가능한 지원(Allowable Assistance), 완료 기준(Completion Criteria), 종료 규칙(Termination Rule)을 명시해야 한다. 성공적인 실행(Successful Execution)은 안전 제약 조건(Safety Constraint)과 시간 제약 조건(Timing Constraint)을 포함한 모든 필수 요구 사항(Mandatory Requirement)을 충족해야 한다. 평가는 완전한 성공(Complete Success), 부분 완료(Partial Completion), 복구 가능한 실패(Recoverable Failure), 복구 불가능한 임무 실패(Irreversible Mission Failure)를 구분해야 한다.

실패 의존성(Failure Dependency)은 임무 길이(Mission Length)가 증가함에 따라 더욱 중요해진다. 임무가 여러 순차적 하위 작업(Sequential Subtask)을 요구할 경우 작은 실패 확률(Failure Probability)도 누적되어 상당한 임무 수준 위험(Mission-Level Risk)을 초래할 수 있다. 그러나 실패 사이에 상관관계(Correlation)가 존재하거나 복구(Recovery)가 가능한 경우 개별 성공률(Individual Success Rate)을 단순히 곱하는 방식은 잘못된 결과를 낳을 수 있다. 평가는 전체 신뢰성(Overall Reliability)을 추정할 때 작업 의존성(Task Dependency), 공통 실패 원인(Shared Failure Cause), 복구 메커니즘(Recovery Mechanism)을 모델링해야 한다.

결함 허용성(Fault Tolerance)은 외란(Disturbance)이나 일부 구성 요소 고장(Partial Component Failure)에도 불구하고 연속 운영(Continuous Operation)을 가능하게 한다. 중복 센서(Redundant Sensor), 대체 제어 전략(Alternative Control Strategy), 상태 감시(Health Monitoring), 점진적 성능 저하(Graceful Degradation)는 필수 기능(Essential Function)을 유지할 수 있다. 로봇은 제한적인 센서 성능 저하(Limited Sensor Performance)를 감지한 이후 속도를 낮추어 임무를 계속할 수 있다. 평가는 성능이 저하된 상태의 운영(Degraded Operation)이 단순히 시스템 종료를 피하는 수준을 넘어 안전하고 생산적이며 임무 요구 사항(Mission Requirement)에 부합하는지 판단해야 한다.

복구 효과(Recovery Effectiveness)는 임무 신뢰성(Mission Reliability)에 큰 영향을 미친다. 실패를 감지하고 유효한 세계 상태(Valid World State)를 복원하며 장애물을 우회하도록 재계획(Replanning)할 수 있는 시스템은 반복적인 외란에도 임무를 완료할 수 있다. 그러나 복구 시도(Recovery Attempt)는 시간(Time), 에너지(Energy), 연산 자원(Computational Resource)을 소비한다. 평가는 성공적으로 복구된 실패의 비율(Proportion of Successfully Recovered Failures), 복구 지연 시간(Recovery Latency), 손실된 작업 진전(Lost Progress), 복구가 최종 임무 결과(Final Mission Outcome)에 미치는 영향을 측정해야 한다.

연속 운영(Continuous Operation)은 임무 전체에 걸쳐 효과적인 자원 관리(Resource Management)를 요구한다. 배터리 용량(Battery Capacity), 열적 한계(Thermal Limit), 연산 부하(Computational Load), 저장 공간 가용성(Storage Availability), 네트워크 대역폭(Network Bandwidth)은 지속적인 실행(Sustained Execution)을 제한할 수 있다. 로봇은 자원 부족(Resource Shortage)을 예측하고 중요한 목표를 방해하지 않으면서 충전(Charging), 냉각(Cooling), 유지보수(Maintenance)를 계획해야 한다. 평가는 자원 계획(Resource Planning)이 임무 실행 가능성(Mission Feasibility)을 유지하고 예방 가능한 중단(Avoidable Interruption)을 방지하는지 판단해야 한다.

임무 신뢰성(Mission Reliability)은 유지보수(Maintenance)와 계획된 운영 중단(Planned Operational Pause)을 고려해야 한다. 충전(Charging), 보정(Calibration), 검사(Inspection), 구성 요소 교체(Component Replacement)는 지속적인 배치(Sustained Deployment)에 필요할 수 있다. 이러한 활동은 예상하지 못한 고장(Unexpected Failure) 및 비상 개입(Emergency Intervention)과 구분해야 한다. 평가 절차(Evaluation Protocol)는 계획된 가동 중단 시간(Planned Downtime)을 자율 운영 시간(Autonomous Operating Time)에서 제외할지 정의하는 동시에 전체 임무 지속 시간(Total Mission Duration)과 운영 가용성(Operational Availability)에 미치는 영향은 반영해야 한다.

안전성(Safety)은 신뢰할 수 있는 연속 운영(Reliable Continuous Operation)의 필수 조건이다. 충돌 제약 조건(Collision Constraint)을 반복적으로 위반하거나 액추에이터 한계(Actuator Limit)를 초과하면서 작업을 완료하는 로봇은 신뢰할 수 있다고 평가할 수 없다. 장시간 시험(Long-Duration Testing)은 누적 안전 노출(Cumulative Safety Exposure), 아차 사고(Near Miss), 비상 정지(Emergency Stop), 제약 조건 위반(Constraint Violation)을 감시해야 한다. 평가는 필수 안전 요구 사항(Mandatory Safety Requirement)을 선택적인 성능 지표(Optional Performance Indicator)가 아니라 임무 성공 조건(Mission Success Condition)으로 취급해야 한다.

신뢰성 평가(Reliability Assessment)는 시간 기반 지표(Time-Based Metric)와 임무 기반 지표(Mission-Based Metric)를 모두 포함해야 한다. 유용한 지표에는 가동 시간 비율(Uptime Ratio), 생산적 자율 운영 비율(Productive Autonomy Ratio), 임무 완료율(Mission Completion Rate), 평균 고장 간 시간(Mean Time Between Failures), 평균 복구 시간(Mean Time to Recovery), 개입 빈도(Intervention Frequency)가 포함된다. 각 지표는 서로 다른 운영 특성(Operational Characteristic)을 포착한다. 평가는 가중치 가정(Weighting Assumption)과 그에 따른 상충 관계(Tradeoff)를 설명하지 않은 채 이러한 측정값을 하나의 점수(Single Score)로 결합해서는 안 된다.

장기 신뢰성(Long-Horizon Reliability)은 생존 분석(Survival Analysis)과 반복 사건 통계(Repeated-Event Statistics)를 활용하여 분석할 수 있다. 고장까지의 시간 분포(Time-to-Failure Distribution)는 시스템이 중대한 중단(Significant Disruption) 이전에 얼마나 오래 작동하는지 보여주며, 반복 사건 모델(Repeated-Event Model)은 되풀이되는 결함(Recurring Fault)을 설명한다. 고장 없이 종료된 임무는 실패로 분류하는 대신 검열 관측값(Censored Observation)으로 반영할 수 있다. 평가는 관측 지속 시간(Observation Duration), 사건 정의(Event Definition), 불확실성 추정값(Uncertainty Estimate), 충분한 시험 노출량(Trial Exposure)을 보고해야 한다.

벤치마크 환경(Benchmark Environment)은 장시간에 걸쳐 현실적인 운영 변동성(Operational Variability)을 도입해야 한다. 조명 변화(Lighting Change), 이동 장애물(Moving Obstacle), 네트워크 외란(Network Disturbance), 적재 하중 변화(Payload Variation), 점진적인 센서 성능 저하(Gradual Sensor Degradation)는 단기 시험에서 발견되지 않는 취약점을 드러낼 수 있다. 통제된 외란(Controlled Disturbance)은 비교를 가능하게 하며, 대표적인 현장 시험(Representative Field Trial)은 실제 적용 가능성(Practical Relevance)을 보여준다. 평가는 로봇 자체에서 발생한 실패와 지정된 운영 영역(Specified Operating Domain) 밖에서 발생한 실패를 구분해야 한다.

연속 운영(Continuous Operation)은 일관된 임무 상태 관리(Consistent Mission State Management)도 요구한다. 일시 정지(Pause), 재시작(Restart), 복구 절차(Recovery Procedure) 이후 로봇은 완료된 작업(Completed Work), 작업 의존성(Task Dependency), 남은 목표(Remaining Objective)를 보존해야 한다. 실행 문맥(Execution Context)을 잘못 복원하면 행동 중복(Duplicated Action)이나 하위 작업 누락(Omitted Subtask)이 발생할 수 있다. 평가는 시스템이 유효한 체크포인트(Valid Checkpoint)에서 실행을 재개하고 중단 전후에 세계 상태 일관성(World State Consistency)을 유지하는지 검증해야 한다.

군집 수준 신뢰성(Fleet-Level Reliability)은 개별 로봇 성능(Individual Robot Performance)을 넘어서는 추가적인 고려 사항을 포함한다. 공유 인프라 고장(Shared Infrastructure Failure), 통신 혼잡(Communication Congestion), 조정된 작업 의존성(Coordinated Task Dependency)은 여러 로봇에 동시에 영향을 미칠 수 있다. 작업을 효과적으로 재분배(Task Redistribution)할 수 있다면 개별 로봇에 고장이 발생하더라도 로봇 군집(Robot Fleet)은 높은 전체 생산성(Aggregate Productivity)을 유지할 수 있다. 평가는 집단 임무 완료(Collective Mission Completion), 서비스 연속성(Service Continuity), 상관된 실패(Correlated Failure)의 결과를 측정해야 한다.

장시간 평가(Long-Duration Evaluation)는 최종 평균값(Final Average)에만 의존하지 않고 신뢰성 추세(Reliability Trend)를 검토해야 한다. 고장률(Failure Rate)은 구성 요소 마모(Component Wear), 환경 노출(Environmental Exposure), 누적된 소프트웨어 상태(Accumulated Software State)에 따라 증가할 수 있다. 반대로 적응형 시스템(Adaptive System)이 반복적인 외란(Recurring Disturbance)으로부터 학습하면 성능이 향상될 수도 있다. 평가는 연속적인 운영 기간(Successive Operating Period)에 걸쳐 신뢰성을 분석하고 실제 개선(Genuine Improvement)을 작업 난이도(Task Difficulty)나 개입 정책(Intervention Policy)의 변화와 구분해야 한다.

궁극적으로 연속 운영 및 임무 신뢰성(Continuous Operation and Mission Reliability)은 피지컬 인공지능(Physical AI) 시스템이 통제된 시연(Controlled Demonstration)을 넘어 신뢰할 수 있는 성능(Dependable Performance)을 제공할 수 있는지 결정한다. 포괄적인 평가(Comprehensive Evaluation)는 임무 완료(Mission Completion), 운영 가용성(Operational Availability), 결함 허용성(Fault Tolerance), 복구(Recovery), 안전성(Safety), 자원 지속 가능성(Resource Sustainability)을 통합해야 한다. 핵심 목표는 자율 시스템(Autonomous System)이 허용 가능한 위험(Acceptable Risk)과 운영 효율성(Operational Efficiency)을 유지하면서 현실적인 조건(Realistic Condition)에서 복잡한 임무(Complex Mission)를 일관되게 수행할 수 있는지 확인하는 것이다.

## 06.14. Efficiency vs Task Completion Tradeoffs

![](images/image15.png){width="7.268055555555556in" height="7.268055555555556in"}

효율성(Efficiency)과 작업 완료(Task Completion)는 장기 피지컬 인공지능(Long-Horizon Physical AI) 평가에서 서로 상충하는 목표(Competing Objective)를 나타낸다. 로봇은 천천히 이동하고, 관측을 반복하며, 광범위한 검증(Extensive Verification)을 수행함으로써 임무를 안정적으로 완료할 수 있지만, 이러한 예방 조치는 실행 시간(Execution Time)과 자원 소비(Resource Consumption)를 증가시킨다. 반대로 공격적인 최적화(Aggressive Optimization)는 속도를 향상시키는 동시에 실패 위험(Failure Risk)을 증가시킬 수 있다. 평가는 효율성 향상(Efficiency Gain)이 요구되는 임무 성공 수준(Mission Success Level)을 유지하는지 판단해야 한다.

작업 완료(Task Completion)는 로봇이 지정된 조건에서 할당된 목표(Assigned Objective)를 달성하는지 측정한다. 효율성(Efficiency)은 이러한 목표를 달성하는 동안 소비되는 자원을 나타내며, 여기에는 시간(Time), 에너지(Energy), 연산 자원(Computation), 물리적 작업량(Physical Effort)이 포함된다. 이러한 차원(Dimension)은 상호 관계를 검토하기 전에 개별적으로 평가해야 한다. 필수 요구 사항(Mandatory Requirement)을 위반하면서 빠르게 작업을 완료하는 시스템은 안전하게 임무를 완료하는 시스템보다 효과적이라고 평가할 수 없다.

장기 임무(Long-Horizon Mission)는 초기 의사결정(Early Decision)이 이후의 기회(Opportunity)와 제약 조건(Constraint)에 영향을 미치기 때문에 효율성 상충 관계(Efficiency Tradeoff)를 증폭시킨다. 짧지만 신뢰성이 낮은 경로(Unreliable Route)를 선택한 로봇은 이동 거리 감소로 얻은 시간 절약보다 더 큰 지연을 경험할 수 있다. 마찬가지로 중간 검증 단계(Intermediate Verification Step)를 생략하면 초기 진행 속도는 높아지지만 이후에 많은 비용이 드는 복구(Recovery)가 필요할 수 있다. 평가는 각 행동을 개별적으로 판단하는 대신 후속 결과(Downstream Consequence)를 고려해야 한다.

실행 시간(Execution Time)은 주요 효율성 지표(Primary Efficiency Measure)이지만, 이를 해석하려면 신중한 정규화(Normalization)가 필요하다. 전체 임무 지속 시간(Total Mission Duration)에는 계획(Planning), 이동(Movement), 조작(Manipulation), 대기(Waiting), 복구(Recovery), 인간 지원(Human Assistance)이 포함될 수 있다. 실제 이동 시간(Active Motion Time)만 보고하면 상당한 운영 지연(Operational Delay)이 감춰질 수 있다. 평가는 종단 간 임무 지속 시간(End-to-End Mission Duration)을 유지하면서 생산적 실행(Productive Execution), 필요한 준비(Necessary Preparation), 불필요한 대기(Avoidable Waiting), 복구 오버헤드(Recovery Overhead)를 구분해야 한다.

에너지 효율성(Energy Efficiency)은 임무가 개별 배터리 주기(Battery Cycle)를 넘어 장시간 지속될수록 더욱 중요해진다. 빠른 움직임은 더 높은 전력(Power)을 요구할 수 있으며, 보수적인 궤적(Conservative Trajectory)은 순간적인 에너지 소비(Instantaneous Energy Consumption)를 줄이지만 운영 시간을 증가시킬 수 있다. 추가적인 센싱(Sensing)과 연산(Computation)도 전체 에너지 소비(Total Energy Consumption)에 기여한다. 평가는 전력이나 이동 거리에만 의존하는 대신 완료된 임무당 에너지(Energy per Completed Mission)와 유용한 작업 결과(Useful Task Outcome)를 기준으로 측정해야 한다.

연산 효율성(Computational Efficiency)은 의사결정 품질(Decision Quality)과 운영 대응성(Operational Responsiveness) 사이에 또 다른 상충 관계를 발생시킨다. 광범위한 계획(Extensive Planning)은 더 안전하거나 짧은 행동 시퀀스(Action Sequence)를 생성할 수 있지만 처리 시간(Processing Time)과 에너지(Energy)를 소비한다. 경량 정책(Lightweight Policy)은 빠르게 대응할 수 있지만 먼 미래의 의존성(Distant Dependency)을 놓칠 수 있다. 평가는 동일한 하드웨어(Hardware)와 환경 조건(Environmental Condition)에서 계획 지연 시간(Planning Latency), 연산 요구량(Computational Demand), 실행 품질(Execution Quality), 최종 완료 확률(Final Completion Probability)을 비교해야 한다.

신뢰성(Reliability)과 효율성(Efficiency)은 실패 비용(Failure Cost)을 통해 상호작용한다. 정상 조건에서 실행 속도가 빠른 전략(Rapid Nominal Execution Strategy)이라도 실패한 시도가 반복적인 조작(Repeated Manipulation), 내비게이션 복구(Navigation Recovery), 임무 재시작(Mission Restart)을 요구하면 전체 성능이 낮아질 수 있다. 따라서 기대 완료 비용(Expected Completion Cost)에는 실패 확률(Failure Probability)과 복구 비용(Recovery Expenditure)이 포함되어야 한다. 평가는 성공한 시험(Successful Trial)의 효율성과 실패한 실행(Unsuccessful Execution)을 포함한 모든 시도(All Attempt)의 효율성을 구분해야 한다.

반복 검증(Repeated Verification)은 신중함(Caution)과 생산성(Productivity) 사이의 균형을 보여준다. 로봇은 매번 조작(Manipulation)을 수행한 후 물체 배치(Object Placement)를 검사하여 오류 감지(Error Detection)를 개선할 수 있지만, 이로 인해 주기 시간(Cycle Time)이 증가한다. 검사 빈도(Inspection Frequency)를 줄이면 오버헤드(Overhead)는 감소하지만 오류가 전파(Error Propagation)될 수 있다. 평가는 검증 빈도(Verification Frequency)가 감지되지 않은 오류(Undetected Error)의 결과에 적합한지, 선택적 감시(Selective Monitoring)가 일률적인 검사(Uniform Checking)보다 더 나은 균형을 제공하는지 판단해야 한다.

안전 요구 사항(Safety Requirement)은 효율성 최적화(Efficiency Optimization)에 타협할 수 없는 제약 조건(Nonnegotiable Constraint)을 부과한다. 로봇은 완료 시간을 단축하기 위해 사람과의 안전 이격 거리(Human Clearance)를 줄이거나, 액추에이터 한계(Actuator Limit)를 초과하거나, 필수 안전 점검(Essential Safety Check)을 생략해서는 안 된다. 평가는 필수 안전 조건(Mandatory Safety Condition)을 임의의 벌점(Arbitrary Penalty)을 부여하는 대상이 아니라 실행 가능성 요구 사항(Feasibility Requirement)으로 취급해야 한다. 효율성 비교는 요구되는 안전 범위(Safety Envelope)를 충족하는 전략 사이에서만 의미가 있다.

부분 완료(Partial Completion)는 모든 목표가 달성되기 전에 임무가 종료될 수 있기 때문에 효율성 측정(Efficiency Measurement)을 복잡하게 만든다. 여러 개의 쉬운 하위 작업(Easy Subtask)을 빠르게 완료하는 로봇이 핵심 의존성(Critical Dependency)을 따라 더 느리게 진행하는 로봇보다 자동으로 우수하다고 평가되어서는 안 된다. 평가는 검증된 진행 정도(Verified Progress), 하위 목표 중요도(Subgoal Importance), 남은 임무의 실행 가능성(Remaining Mission Feasibility)을 측정해야 한다. 부분 진행 지표(Partial Progress Metric)는 최종 목표(Final Objective)를 향해 진전하지 않는 단순한 활동(Activity)을 보상하지 않도록 설계해야 한다.

시간 제약 임무(Time-Constrained Mission)는 속도(Speed)와 마감 시간 준수 확률(Probability of Meeting Deadlines) 사이의 균형을 요구한다. 보수적인 전략(Conservative Strategy)은 최종적인 성공 가능성(Eventual Success)을 높일 수 있지만 완료 시점이 너무 늦으면 실패할 수 있다. 빠른 전략(Faster Strategy)은 개별 행동 실패 확률(Individual Action Failure Probability)이 더 높더라도 마감 시간을 충족하는 경우가 많을 수 있다. 평가는 최종 완료 확률(Eventual Completion Probability)과 마감 시간 제약 임무 성공(Deadline-Constrained Mission Success)을 구분하고 동일한 시간 요구 사항(Timing Requirement)에서 두 가지를 모두 평가해야 한다.

자원 할당 결정(Resource Allocation Decision)도 미래 임무 실행 가능성(Future Mission Feasibility)에 영향을 미친다. 초기 작업 정확도(Early Task Accuracy)를 높이기 위해 추가 에너지를 소비하면 이후 내비게이션(Navigation)이나 조작(Manipulation)에 사용할 수 있는 자원이 감소할 수 있다. 반대로 과도한 자원 절약(Excessive Resource Conservation)은 작업 진행을 불필요하게 지연시킬 수 있다. 평가는 자원 인식 정책(Resource-Aware Policy)이 비효율적인 과잉 자원 확보(Overprovisioning)와 불필요한 운영 중단(Unnecessary Operational Pause)을 피하면서 충분한 예비 자원(Resource Reserve)을 유지하는지 검토해야 한다.

파레토 분석(Pareto Analysis)은 단일 선호도(Single Preference)를 강요하지 않으면서 효율성과 작업 완료 사이의 상충 관계를 검토할 수 있는 유용한 프레임워크(Framework)를 제공한다. 다른 전략이 적어도 동일한 작업 성공(Task Success)을 더 많은 자원 비용(Resource Cost) 없이 달성하면서 하나 이상의 차원을 개선한다면 해당 전략은 파레토 지배(Pareto Dominance)를 받는다. 지배되지 않는 전략(Nondominated Strategy)은 파레토 전선(Pareto Frontier)을 형성한다. 평가는 이러한 대안을 보고하여 배치 요구 사항(Deployment Requirement)에 따라 적절한 운영 지점(Operating Point)을 결정할 수 있도록 해야 한다.

복합 효율성 점수(Composite Efficiency Score)는 비교를 단순화할 수 있지만 중요한 차이를 감출 수 있다. 완료율(Completion Rate), 실행 시간(Execution Time), 에너지(Energy), 개입 부담(Intervention Burden)을 가중 결합(Weighted Combination)하는 방식은 주관적인 우선순위(Subjective Priority)에 의존한다. 속도의 작은 개선(Small Speed Improvement)이 신뢰성의 상당한 감소(Substantial Reliability Reduction)를 자동으로 보상해서는 안 된다. 평가는 통합 순위(Aggregate Ranking)를 해석하기 전에 정규화 방법(Normalization Method), 가중치 가정(Weighting Assumption), 대체 선호도(Alternative Preference)에 대한 민감도(Sensitivity)를 공개해야 한다.

위험 민감 평가(Risk-Sensitive Evaluation)는 평균 성능(Average Performance)뿐 아니라 드물지만 비용이 큰 실패(Rare Costly Failure)의 결과도 고려한다. 두 정책(Policy)은 평균 완료 시간(Mean Completion Time)이 유사하더라도 한 정책은 간헐적으로 심각한 지연(Severe Delay)이나 임무 종료(Mission Termination)를 경험할 수 있다. 꼬리 지연 시간(Tail Latency), 완료 시간 변동성(Completion-Time Variability), 최악 조건의 자원 소비(Worst-Case Resource Expenditure)는 평균값에 숨겨진 운영 위험(Operational Risk)을 드러낸다. 이러한 측정값은 안전 필수 배치(Safety-Critical Deployment)나 마감 시간에 민감한 배치(Deadline-Sensitive Deployment)에서 특히 중요하다.

적응형 효율성 정책(Adaptive Efficiency Policy)은 작업 난이도(Task Difficulty)와 환경 불확실성(Environmental Uncertainty)에 따라 행동을 조정할 수 있다. 로봇은 익숙하고 개방된 공간(Familiar Open Space)에서는 빠르게 이동하면서 사람이나 불확실한 장애물(Uncertain Obstacle) 근처에서는 속도를 낮출 수 있다. 또한 조작 신뢰도(Manipulation Confidence)가 감소하면 검증(Verification)을 강화할 수 있다. 평가는 이러한 적응(Adaptation)이 고정 속도(Fixed-Speed), 고정 검증(Fixed-Verification), 일률적으로 보수적인 정책(Uniformly Conservative Policy)보다 전체 임무 결과(Overall Mission Outcome)를 개선하는지 판단해야 한다.

벤치마크 설계(Benchmark Design)는 변화하는 상충 관계(Changing Tradeoff)를 드러내기 위해 임무 길이(Mission Length), 작업 의존성(Task Dependency), 자원 제한(Resource Limit), 외란 빈도(Disturbance Frequency)를 다양하게 설정해야 한다. 단기 시험(Short Test)은 지연된 실패(Delayed Failure)가 관측되지 않기 때문에 공격적인 전략(Aggressive Strategy)에 유리할 수 있다. 장기 시험(Extended Trial)은 누적된 복구 비용(Accumulated Recovery Cost)과 자원 고갈(Resource Depletion)을 드러낸다. 평가는 동일한 운영 노출량(Operational Exposure)과 완료 요구 사항(Completion Requirement)에서 전략을 비교하기 위해 대응되는 시나리오(Matched Scenario)와 반복 시험(Repeated Trial)을 사용해야 한다.

인간 지원(Human Assistance)은 외부 개입(External Intervention)이 운영 자원(Operational Resource)을 소비하기 때문에 효율성 계산(Efficiency Accounting)에 포함되어야 한다. 빈번한 운영자 수정(Operator Correction)을 통해 작업을 빠르게 완료하는 로봇은 인간 노동(Human Labor)을 무시하면 효율적으로 보일 수 있다. 평가는 자율 실행 시간(Autonomous Execution Time), 지원 시간(Assisted Time), 개입 빈도(Intervention Frequency), 운영자 작업 부담(Operator Workload)을 보고해야 한다. 이를 통해 인간 지원 성능(Human-Supported Performance)이 독립적인 로봇 효율성(Independent Robotic Efficiency)으로 잘못 해석되는 것을 방지할 수 있다.

통계 분석(Statistical Analysis)은 완료되지 않은 임무(Incomplete Mission)와 반복 시험(Repeated Trial) 사이의 변동성(Variability)을 고려해야 한다. 성공한 실행(Successful Run)에 대해서만 평균 완료 시간(Average Completion Time)을 보고하면 실패율(Failure Rate)이 서로 다른 경우 선택 편향(Selection Bias)이 발생한다. 평가는 성공 확률(Success Probability), 완료 시간 분포(Completion-Time Distribution), 자원 소비(Resource Consumption), 실패하거나 검열된 시험(Failed or Censored Trial)에 대한 명확한 처리 기준을 제공해야 한다. 신뢰 구간(Confidence Interval)은 관측된 효율성 개선(Apparent Efficiency Improvement)이 의미 있는지 판단하는 데 도움이 된다.

궁극적으로 효율성과 작업 완료 사이의 상충 관계 평가(Efficiency versus Task Completion Evaluation)는 피지컬 인공지능(Physical AI) 시스템이 신뢰성(Reliability)과 안전성(Safety)을 유지하면서 허용 가능한 자원 소비(Acceptable Resource Expenditure)로 복잡한 임무(Complex Mission)를 수행할 수 있는지 판단한다. 목표는 단순히 실행 시간(Execution Time)을 최소화하거나 성공률(Success Rate)을 독립적으로 극대화하는 것이 아니다. 포괄적인 평가(Comprehensive Assessment)는 현실적인 장기 운영 조건(Realistic Long-Horizon Condition)에서 임무 완료(Mission Completion), 자원 지속 가능성(Resource Sustainability), 복구 비용(Recovery Cost), 배치 제약 조건(Deployment Constraint) 사이의 균형을 달성하는 운영 전략(Operating Strategy)을 식별한다.

## 06.15. Long Horizon Evaluation Framework [w/Code]

![](images/image16.png){width="7.268055555555556in" height="7.268055555555556in"}

장기 평가 프레임워크(Long-Horizon Evaluation Framework)는 피지컬 인공지능(Physical AI) 시스템이 지속적인 자율 운영(Sustained Autonomous Operation)을 통해 복잡한 임무(Complex Mission)를 완료할 수 있는지 평가하기 위한 체계적인 방법을 제공한다. 개별 기술 벤치마크(Isolated Skill Benchmark)와 달리 상호 의존적인 행동 시퀀스(Interdependent Action Sequence), 환경 변화(Environmental Change), 누적된 실행 오류(Accumulated Execution Error)를 검토한다. 이 프레임워크는 작업 성공(Task Success), 계획 일관성(Planning Consistency), 복구 역량(Recovery Capability), 운영 신뢰성(Operational Reliability), 자원 효율성(Resource Efficiency)을 재현 가능한 평가 과정(Reproducible Evaluation Process)에 통합해야 한다.

프레임워크의 기반은 목표(Objective), 초기 조건(Initial Condition), 환경 제약 조건(Environmental Constraint), 완료 기준(Completion Criteria)을 정의하는 공식적인 임무 명세(Formal Mission Specification)이다. 각 임무는 관측 가능한 성공 조건(Observable Success Condition)과 명시적인 실패 경계(Explicit Failure Boundary)를 포함해야 한다. 평가자는 필수 결과(Mandatory Outcome)와 선택적인 성능 개선(Optional Performance Improvement)을 구분해야 한다. 명확한 명세(Clear Specification)는 모호한 점수 산정(Ambiguous Scoring)을 방지하고 서로 다른 시스템이 동등한 운영 요구 사항(Equivalent Operational Requirement)에 따라 평가되도록 보장한다.

임무 분해(Mission Decomposition)는 장시간 실행 과정에서 진행 정도(Progress)를 평가하는 데 필요한 중간 구조(Intermediate Structure)를 확립한다. 복잡한 목표(Complex Objective)는 의존성(Dependency), 선행 조건(Prerequisite), 측정 가능한 완료 조건(Measurable Completion Condition)을 갖는 하위 작업(Subtask)으로 표현된다. 이러한 구조를 통해 평가자는 작업 진행이 발생하는 지점과 실패가 전파되는 지점을 식별할 수 있다. 프레임워크는 성공적인 중간 행동(Successful Intermediate Action)과 전체 임무 목표(Overall Mission Objective)의 달성을 구분해야 한다.

시간적 평가(Temporal Evaluation)는 임무가 진행됨에 따라 성능이 어떻게 변화하는지 포착한다. 초기 의사결정(Early Decision)은 이후 실행 가능성(Later Feasibility)에 영향을 미칠 수 있으며, 작은 오류(Small Error)가 누적되어 심각한 중단(Significant Disruption)을 초래할 수 있다. 프레임워크는 작업 전환(Task Transition), 경과 시간(Elapsed Time), 실행 지연(Execution Delay), 주요 사건 발생 시점(Critical Event Timing)을 기록해야 한다. 시간적 측정(Temporal Measurement)은 시스템이 일관된 성능(Consistent Performance)을 유지하는지 또는 장시간 자율 운영(Prolonged Autonomous Operation) 중 효과가 점진적으로 감소하는지 판단하는 데 도움이 된다.

상태 일관성 평가(State Consistency Evaluation)는 로봇이 환경(Environment)과 작업 진행 상태(Task Progress)에 대한 정확한 표현을 유지하는지 검토한다. 물체 위치(Object Location), 완료된 행동(Completed Action), 자원 가용성(Resource Availability), 남은 목표(Remaining Objective)는 물리적 현실(Physical Reality)과 동기화된 상태를 유지해야 한다. 잘못된 상태 추정값(Incorrect State Estimate)은 반복적인 행동(Repeated Action)이나 유효하지 않은 계획(Invalid Plan)을 초래할 수 있다. 프레임워크는 정의된 체크포인트(Checkpoint)에서 내부 상태 표현(Internal State Representation)을 독립적인 관측(Independent Observation)과 비교해야 한다.

계획 및 재계획 평가(Planning and Replanning Assessment)는 시스템이 실행 가능한 행동 시퀀스(Feasible Action Sequence)를 생성하고 조건이 변화할 때 이를 수정하는 능력을 측정한다. 예상하지 못한 장애물(Unexpected Obstacle), 사용할 수 없는 자원(Unavailable Resource), 실패한 하위 작업(Failed Subtask)은 적절한 적응(Adaptation)을 유발해야 한다. 평가는 정당한 계획 수정(Justified Plan Revision)과 불안정한 의사결정(Unstable Decision-Making)을 구분해야 한다. 유용한 측정값에는 계획 지연 시간(Planning Latency), 수정 빈도(Revision Frequency), 의존성 보존(Dependency Preservation), 외란 이후 성공적인 작업 지속(Successful Continuation after Disturbances)이 포함된다.

실패 감지 및 복구(Failure Detection and Recovery)는 또 다른 필수 평가 차원(Evaluation Dimension)을 형성한다. 시스템은 예상 결과(Expected Outcome)와 관측 결과(Observed Outcome) 사이의 편차(Deviation)를 식별하고 원인을 판단하며 적절한 수정 행동(Corrective Action)을 선택해야 한다. 복구에는 국소적 조정(Local Adjustment), 전역 재계획(Global Replanning), 인간 지원(Human Assistance)이 포함될 수 있다. 프레임워크는 감지 지연 시간(Detection Latency), 진단 정확도(Diagnosis Accuracy), 복구 성공(Recovery Success), 실패 이후 보존된 임무 진행 정도(Preserved Mission Progress)를 측정해야 한다.

인간 개입(Human Intervention)은 자율성 평가(Autonomy Assessment)에 명시적으로 포함되어야 한다. 반복적인 운영자 수정(Operator Correction)을 통해 완료된 임무는 지원 없이 완료된 임무와 동일한 독립성(Independence)을 입증하지 않는다. 평가는 개입 빈도(Intervention Frequency), 지속 시간(Duration), 목적(Purpose), 제어권 이전(Control Transfer)을 기록해야 한다. 이러한 관측은 개입률(Intervention Rate), 지원 시간 비율(Assisted-Time Fraction), 자율 운영 지속 시간(Autonomy Duration), 평균 개입 간 시간(Mean Time Between Interventions)과 같은 지표를 지원한다.

연속 운영 평가(Continuous Operation Evaluation)는 장시간에 걸쳐 자율 성능(Autonomous Performance)이 신뢰할 수 있는 수준으로 유지되는지 판단한다. 센서 성능 저하(Sensor Degradation), 위치 추정 드리프트(Localization Drift), 연산 제한(Computational Limitation), 자원 고갈(Resource Depletion)은 장기 임무(Long Mission)에서만 나타날 수 있다. 프레임워크는 생산적 운영 시간(Productive Operating Time), 예상하지 못한 중단(Unexpected Interruption), 복원 시간(Restoration Time), 임무 완료 신뢰성(Mission Completion Reliability)을 측정해야 한다. 장시간 시험(Long-Duration Trial)은 짧은 시연(Short Demonstration)에서 드러나지 않는 취약점을 노출해야 한다.

효율성 평가(Efficiency Assessment)는 임무 결과(Mission Outcome)를 해당 결과를 달성하는 데 필요한 자원(Resource)과 연결한다. 실행 시간(Execution Time), 에너지 소비(Energy Consumption), 연산 요구량(Computational Demand), 이동 거리(Travel Distance), 복구 오버헤드(Recovery Overhead)는 작업 완료(Task Completion)와 함께 측정해야 한다. 빠른 실행(Faster Execution)이 실패 확률(Failure Probability)을 높이거나 안전 요구 사항(Safety Requirement)을 위반한다면 반드시 더 바람직한 것은 아니다. 프레임워크는 효율성과 신뢰성 사이의 상충 관계(Efficiency and Reliability Tradeoff)를 검토해야 하며 어느 한 차원만 독립적으로 최적화해서는 안 된다.

안전 요구 사항(Safety Requirement)은 평가 전 과정에서 필수 제약 조건(Mandatory Constraint)으로 취급해야 한다. 충돌 회피(Collision Avoidance), 액추에이터 제한(Actuator Limitation), 제한된 운영 구역(Restricted Operating Region), 안전한 복구 절차(Safe Recovery Procedure)는 정상 실행(Normal Execution)과 예상하지 못한 외란(Unexpected Disturbance) 상황 모두에서 유효하게 유지되어야 한다. 안전하지 않은 행동(Unsafe Behavior)을 통해 목표를 달성한 임무에는 제한 없는 성공 판정(Unrestricted Success Classification)을 부여해서는 안 된다. 안전 위반(Safety Violation)은 작업 진행(Task Progress) 및 효율성(Efficiency)과 독립적으로 기록해야 한다.

벤치마크 시나리오(Benchmark Scenario)는 점진적으로 증가하는 임무 복잡도(Mission Complexity)와 환경 불확실성(Environmental Uncertainty)을 포괄해야 한다. 초기 시험(Initial Test)은 예측 가능한 의존성(Predictable Dependency)을 갖는 구조화된 시퀀스(Structured Sequence)를 포함할 수 있으며, 고급 시나리오(Advanced Scenario)는 동적 장애물(Dynamic Obstacle), 누락된 물체(Missing Object), 지연된 행동(Delayed Action), 자원 제약 조건(Resource Constraint)을 도입한다. 통제된 외란 주입(Controlled Disturbance Injection)은 반복 가능한 비교(Repeatable Comparison)를 지원한다. 프레임워크는 이전에 경험한 상황을 넘어 역량이 일반화되는지 평가하기 위해 익숙하지 않은 조건(Unfamiliar Condition)도 포함해야 한다.

표준화된 실행 절차(Standardized Execution Protocol)는 의미 있는 벤치마킹(Meaningful Benchmarking)을 위해 필요하다. 각 시험(Trial)은 초기화 절차(Initialization Procedure), 무작위화 설정(Randomization Setting), 허용 가능한 지원(Allowable Assistance), 종료 조건(Termination Condition), 관측 방법(Observation Method)을 정의해야 한다. 시뮬레이션(Simulation)과 물리적 시험(Physical Testing)은 실용적인 범위에서 호환 가능한 임무 정의(Compatible Mission Definition)를 사용해야 한다. 동일한 조건에서 수행되는 반복 시험(Repeated Trial)은 실제 역량 차이(Genuine Capability Difference)를 환경 변동성(Environmental Variability) 및 실험 잡음(Experimental Noise)과 구분하는 데 도움이 된다.

평가 데이터(Evaluation Data)는 관측(Observation), 내부 상태(Internal State), 선택된 행동(Selected Action), 작업 전환(Task Transition), 개입(Intervention), 결과(Outcome)를 포함하는 동기화된 로그(Synchronized Log)를 통해 수집해야 한다. 각 사건(Event)은 타임스탬프(Timestamp)와 관련 문맥 정보(Contextual Information)를 포함해야 한다. 자동화된 점수 산정(Automated Scoring)은 주관적인 해석(Subjective Interpretation)을 줄이며, 독립적인 검증(Independent Verification)은 결과의 신뢰성(Result Credibility)을 강화한다. 재현 가능한 기록(Reproducible Record)은 실패 분석(Failure Analysis), 디버깅(Debugging), 모델 버전 간 비교(Model Version Comparison)도 지원한다.

지표 집계(Metric Aggregation)는 장기 자율성(Long-Horizon Autonomy)이 본질적으로 다차원적(Multidimensional)이기 때문에 신중하게 처리해야 한다. 임무 성공(Mission Success), 하위 목표 완료(Subgoal Completion), 개입 부담(Intervention Burden), 복구 효과(Recovery Effectiveness), 안전성(Safety), 효율성(Efficiency)은 먼저 개별적으로 보고해야 한다. 복합 점수(Composite Score)는 비교를 지원할 수 있지만 중요한 취약점(Weakness)을 감출 수 있다. 모든 집계 방법(Aggregation Method)은 정규화 규칙(Normalization Rule), 가중치 가정(Weighting Assumption), 지표 간 상쇄(Metric Compensation)에 따른 결과를 공개해야 한다.

통계적 평가(Statistical Evaluation)는 변동성(Variability), 미완료 임무(Incomplete Mission), 드문 실패(Rare Failure)를 고려해야 한다. 성공 확률(Success Probability)은 반복 시험(Repeated Trial)을 통해 추정해야 하며, 완료 시간 분포(Completion-Time Distribution)와 신뢰 구간(Confidence Interval)은 불확실성(Uncertainty)을 보여준다. 개입 없이 종료된 임무는 자율 운영 지속 시간 분석(Autonomy-Duration Analysis)에서 검열 관측값(Censored Observation)으로 반영할 수 있다. 운영 노출 시간(Exposure Time), 시험 횟수(Trial Count), 실패 정의(Failure Definition)를 보고하는 것은 신뢰성 주장(Reliability Claim)을 해석하는 데 필수적이다.

환경 간 평가(Cross-Environment Evaluation)는 장기 성능(Long-Horizon Performance)이 단일 벤치마크 구성(Single Benchmark Configuration)을 넘어 전이되는지 판단한다. 조명(Lighting), 물체 배치(Object Placement), 지형(Terrain), 로봇 신체 구조(Robot Embodiment), 작업 순서(Task Ordering)의 변화는 숨겨진 의존성(Hidden Dependency)을 드러낼 수 있다. 프레임워크는 익숙한 조건(Familiar Condition)에서의 성능과 익숙하지 않은 환경(Unfamiliar Setting)으로의 일반화(Generalization)를 구분해야 한다. 비교 가능한 평가 절차(Comparable Evaluation Procedure)는 성능 개선이 견고한 자율성(Robust Autonomy)을 반영하는지 아니면 제한적인 벤치마크 적응(Narrow Benchmark Adaptation)에 불과한지 식별하는 데 도움이 된다.

실용적인 구현(Practical Implementation)은 평가 과정을 임무 정의(Mission Definition), 시나리오 생성(Scenario Generation), 실행 감시(Execution Monitoring), 사건 분류(Event Classification), 지표 계산(Metric Computation), 보고서 생성(Report Generation)으로 구성할 수 있다. 각 단계는 임무 요구 사항(Mission Requirement)과 측정된 결과(Measured Outcome) 사이의 추적 가능한 연결(Traceable Connection)을 유지해야 한다. 자동화된 파이프라인(Automated Pipeline)은 시험을 반복하고 로그를 검증하며 표준화된 평가표(Standardized Scorecard)를 생성할 수 있다. 모듈형 설계(Modular Design)는 기존 평가 원칙(Established Evaluation Principle)을 변경하지 않고 새로운 작업과 지표를 도입할 수 있도록 한다.

벤치마크 거버넌스(Benchmark Governance)는 작업(Task), 환경(Environment), 모델(Model)이 발전함에 따라 일관성을 유지하도록 지원한다. 데이터셋 버전(Dataset Version), 시나리오 구성(Scenario Configuration), 점수 산정 규칙(Scoring Rule), 소프트웨어 의존성(Software Dependency)은 모든 평가에서 기록되어야 한다. 비교 가능성(Comparability)에 영향을 미치는 변경 사항은 명시적인 문서화(Explicit Documentation)가 필요하며 경우에 따라 별도의 벤치마크 버전(Benchmark Version)이 요구된다. 이러한 수명주기 관리 원칙(Lifecycle Discipline)은 서로 다른 가정(Assumption)이나 실험 조건(Experimental Condition)에서 얻어진 결과를 잘못 비교하는 것을 방지한다.

궁극적으로 장기 평가 프레임워크(Long-Horizon Evaluation Framework)는 피지컬 인공지능(Physical AI) 시스템이 복잡한 임무(Complex Mission) 전반에서 일관되고 안전하며 생산적인 자율성(Coherent, Safe, and Productive Autonomy)을 지속할 수 있는지 입증해야 한다. 신뢰할 수 있는 평가(Reliable Assessment)는 시간적 진행(Temporal Progress), 계획(Planning), 상태 일관성(State Consistency), 실패 복구(Failure Recovery), 개입 요구 사항(Intervention Requirement), 운영 연속성(Operational Continuity), 효율성(Efficiency)을 통합한다. 이를 통해 얻어진 평가 근거(Evaluation Evidence)는 투명한 비교(Transparent Comparison), 체계적인 개선(Systematic Improvement), 실제 환경 배치 준비도(Real-World Deployment Readiness)에 관한 정보에 기반한 의사결정(Informed Decision-Making)을 지원한다.
