# Team4_BE

Team4_BE는 운동 기록 및 사용자 관리를 위한 백엔드 API 서버입니다. FastAPI를 기반으로 구축되었으며, 사용자 인증, 운동 기록 관리, 마이페이지 기능, 포인트 시스템 등을 제공합니다.

## 주요 기능 및 API 엔드포인트

### 1. 서버 상태 확인 (Check Server)
- **서버 및 API 상태 확인:** 데이터베이스 연결 상태를 포함한 서버의 전반적인 상태를 확인합니다. (`GET /check-server/`)

### 2. 사용자 관리 (User)
- **유저 생성:** 새로운 사용자를 등록합니다. (`POST /user/create-user`)
- **유저 상세 정보 생성:** 사용자 프로필 상세 정보를 추가합니다. (`POST /user/create-user-details`)
- **로그인:** 이메일을 통해 로그인하고 JWT 토큰을 발급받습니다. (`POST /user/login`)
- **로그아웃:** 사용자 토큰을 무효화하여 로그아웃합니다. (`POST /user/logout`)

### 3. 운동 관리 (Exercise)
- **운동 리스트 조회:** 유산소 및 근력 운동 목록을 조회합니다. (`GET /exercise/`)

### 4. 운동 기록 관리 (Exercise Log)
- **운동 기록 추가:** 사용자의 운동 기록을 생성합니다. (`POST /exercise-logs/`)
- **이번 주 운동 기록 조회:** 특정 사용자의 이번 주 운동 기록을 조회합니다. (`GET /exercise-logs/this-week`)
- **특정 날짜 운동 기록 조회:** 원하는 날짜가 포함된 주의 운동 기록을 조회합니다. (`GET /exercise-logs/target-date`)
- **운동 기록 수정:** 운동 기록의 메모 내용을 수정합니다. (`PATCH /exercise-logs/{log_id}`)
- **운동 기록 삭제:** 특정 운동 기록을 삭제합니다. (`DELETE /exercise-logs/{log_id}`)
- **이번 주 근력 운동 횟수 조회:** 특정 사용자의 이번 주 근력 운동 횟수를 반환합니다. (`GET /exercise-logs/strength/count`)

### 5. 마이페이지 (Mypage)
- **유저 조회:** 이메일을 통해 사용자 정보를 조회합니다. (`GET /mypage/get-user`)
- **유저 상세 정보 조회:** 사용자 프로필 상세 정보를 조회합니다. (`GET /mypage/get-user-details`)
- **유저 프로필 수정:** 사용자 프로필 정보를 수정합니다. (`PUT /mypage/edit-user/{user_id}`)
- **유저 안정 심박수 조회:** 사용자의 안정 심박수를 조회합니다. (`GET /mypage/resting-heart-rate`)
- **유저 안정 심박수 설정/수정:** 사용자의 안정 심박수를 설정하거나 수정합니다. (`PUT /mypage/put-resting-heart-rate`)
- **지난 4주간 운동량 조회:** 사용자의 지난 4주간 운동 기록을 조회합니다. (`GET /mypage/get-exercise-logs`)
- **지난 25주간 운동량 조회:** 사용자의 지난 25주간 운동 기록을 조회합니다. (`GET /mypage/get-exercise-logs/25weeks`)
- **프로필 이미지 수정:** 사용자 프로필 이미지를 업로드하고 수정합니다. (`POST /mypage/edit-user/profile-image`)

### 6. 포인트 시스템 (Points)
- **주간 포인트 조회:** 특정 사용자의 한 주간 획득한 포인트를 조회합니다. (`GET /points/{target_date}`)

## 기술 스택
- **Backend Framework:** FastAPI
- **Database:** SQLAlchemy (ORM)
- **Authentication:** JWT (JSON Web Tokens)
- **Deployment:** Docker
- **Cloud Storage:** AWS S3 (프로필 이미지 저장)
- **Monitoring/Logging:** Discord Webhook (서버 상태 및 운동 기록 알림)

## 설정 및 실행

1.  **환경 변수 설정:** `.env` 파일을 생성하고 필요한 환경 변수를 설정합니다. (예: 데이터베이스 연결 정보, AWS S3 키, Discord Webhook URL 등)
2.  **의존성 설치:** `requirements.txt`에 명시된 파이썬 패키지를 설치합니다.
    ```bash
    pip install -r requirements.txt
    ```
3.  **데이터베이스 마이그레이션:** 데이터베이스 스키마를 적용합니다.
    ```bash
    # Alembic 또는 Django Migrations 사용 시 해당 명령어 입력
    # 예: alembic upgrade head
    ```
4.  **애플리케이션 실행:** Uvicorn을 사용하여 애플리케이션을 실행합니다.
    ```bash
    uvicorn main:app --reload
    ```

## API 명세서
자세한 API 명세는 다음 링크를 참조하십시오:
[https://github.com/Drag-on-Park/Team4_BE/wiki/API-%EB%AA%85%EC%84%B8%EC%84%B0](https://github.com/Drag-on-Park/Team4_BE/wiki/API-%EB%AA%85%EC%84%B8%EC%84%B0)
