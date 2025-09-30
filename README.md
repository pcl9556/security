@Lazy 어노테이션
역할

지연 초기화(Lazy Initialization)

스프링은 기본적으로 애플리케이션 시작 시 모든 Bean을 미리 생성함

@Lazy 사용 시 Bean은 실제로 필요할 때 생성됨

순환 참조(Circular Dependency) 해결

의존하면 빈 생성 충돌 가능성 있음

@Lazy로 지정하면, 나중에 필요할 때 주입되므로 충돌을 피할 수 있음

성능 최적화

초기 구동 시 꼭 필요하지 않은 Bean은 생성하지 않으니, 시작 속도 최적화 효과도 있음


Filter 체인

Spring Security는 다양한 Filter들의 체인으로 구성
이 Filter 체인은 Request를 가로챈 후 일련의 절차를 처리
UsernamePasswordAuthenticationFilter는 사용자가 제출한 인증정보 처리

2.2. UsernamePasswordAuthenticationToken 생성

UsernamePasswordAuthenticationFilter는 UsernamePasswordAuthenticationToken을 생성하여 AuthenticationManager에게 전달
이 토큰에는 사용자가 제출한 인증 정보가 포함되어 있음

2.3. AuthenticationManager

AuthenticationManager는 실제로 인증을 수행
여러 AuthenticationProvider들을 이용

2.4. AuthenticationProvider

각각의 Provider들은 특정 유형의 인증을 처리
Ex. DaoAuthenticationProvider는 사용자 정보를 DB에서 가져와 인증을 수행

2.5. PasswordEncoder

인증과 인가에서 사용될 패스워드의 인코딩 방식을 지정

2.6. UserDetailsService

AuthenticationProvider는 UserDetailsService를 사용하여 사용자 정보를 가져옴
UserDetailsService는 사용자의 아이디를 받아 loadByUsername을 호출하여 해당 사용자의 UserDetails를 반환

2.7. UserDetails

UserDetails에는 사용자의 아이디, 비밀번호, 권한 등이 포함

2.8. Authentication 객체 생성

인증에 성공하면, AuthenticationProvider는 Authentication 객체를 생성하여 AuthenticationManager에게 반환
Authentication 객체에는 사용자의 세부 정보와 권한이 포함

2.9. SecurityContextHolder

현재 실행 중인 스레드에 대한 SecurityContext를 제공

2.10. SecurityContext

현재 사용자의 Authentication이 저장되어 있음
애플리케이션은 SecurityContextHolder를 통해 현재 사용자의 권한을 확인하고 인가 결정을 함
