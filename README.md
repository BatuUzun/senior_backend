# senior_backend database

# User database

CREATE TABLE user_profiles (
    id SERIAL PRIMARY KEY,           
    username VARCHAR(255) UNIQUE NOT NULL,  -- Unique username column
    description TEXT,                
    bio TEXT,                        
    link VARCHAR(2083),              
    location VARCHAR(255),           
    profile_image VARCHAR(2083)      
);

CREATE TABLE user_follows (
    follower_id BIGINT NOT NULL REFERENCES user_profiles(id),
    followed_id BIGINT NOT NULL REFERENCES user_profiles(id),
    PRIMARY KEY (follower_id, followed_id)
);



INSERT INTO user_profiles (username, description, bio, link, location, profile_image) VALUES
('john_doe', 'Software Engineer', 'Loves coding and problem-solving.', 'https://johndoe.com', 'New York', 'default.png'),
('jane_smith', 'Graphic Designer', 'Passionate about creativity.', 'https://janesmith.com', 'San Francisco', 'default.png'),
('jack_black', 'Photographer', 'Capturing moments.', 'https://jackblack.com', 'Los Angeles', 'default.png'),
('jill_white', 'Content Writer', 'Storyteller and blogger.', 'https://jillwhite.com', 'Chicago', 'default.png'),
('john_smith', 'Product Manager', 'Leading teams to success.', 'https://johnsmith.com', 'Seattle', 'default.png'),
('johnny_cash', 'Musician', 'Living through music.', 'https://johnnycash.com', 'Nashville', 'default.png'),
('janet_jones', 'Entrepreneur', 'Building innovative solutions.', 'https://janetjones.com', 'Austin', 'default.png'),
('jacob_miller', 'Fitness Trainer', 'Helping people stay fit.', 'https://jacobmiller.com', 'Miami', 'default.png'),
('julia_brown', 'Artist', 'Expressing emotions through art.', 'https://juliabrown.com', 'Portland', 'default.png'),
('johnathon_clark', 'Chef', 'Creating delicious meals.', 'https://johnathonclark.com', 'Boston', 'default.png');




# Interaction database

CREATE TABLE review (
    id BIGSERIAL PRIMARY KEY, 
    user_id BIGINT NOT NULL,  
    rating INT NOT NULL CHECK (rating BETWEEN 1 AND 5), 
    comment TEXT,            
    spotify_id VARCHAR(64) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP 
);

CREATE TABLE likes (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT NOT NULL,
    spotify_id VARCHAR(64) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE favorite (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT NOT NULL,
    spotify_id VARCHAR(64) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
