# senior_backend database

User database

CREATE TABLE user_profiles (
    id SERIAL PRIMARY KEY,           -- Primary key, auto-incremented
    username VARCHAR(255) UNIQUE NOT NULL,  -- Unique username column
    description TEXT,                -- Description column
    bio TEXT,                        -- Bio column
    link VARCHAR(2083),              -- Link column (max length for URLs)
    location VARCHAR(255),           -- Location column, max length of 255 characters
    profile_image VARCHAR(2083)      -- Profile image column to store S3 link
);

CREATE TABLE user_follows (
    follower_id BIGINT NOT NULL REFERENCES user_profiles(id),
    followed_id BIGINT NOT NULL REFERENCES user_profiles(id),
    PRIMARY KEY (follower_id, followed_id)
);



-- Insert sample data into user_profiles
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




Interaction database

CREATE TABLE review (
    id BIGSERIAL PRIMARY KEY, -- Auto-incrementing unique identifier for each review
    user_id BIGINT NOT NULL,  -- User ID associated with the review
    rating INT NOT NULL CHECK (rating BETWEEN 1 AND 5), -- Rating, constrained to values 1 to 5
    comment TEXT,            -- Optional comment provided by the user
    spotify_id VARCHAR(64) NOT NULL, -- Spotify ID (allowing for potential future changes in length)
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP -- Timestamp of when the review was created
);
